---
title: "Kossel XL 构建记 (36) ---- 关于 Kossel 带有自动调平功能的 Marlin 固件"
date: "2015-03-03 15:00:00"
tags: ["3dp", "deltabot", "Kossel", "Marlin", "auto-levelling", "auto-calibration", "G29", "G30"]
draft: false
author: "tt4"
---

#### 自动调平与自动校正

首先要澄清一下，自动调平（auto-leveling）和自动校正（auto-calibration）是两个容易混淆的概念。自动调
平，一般是指调节热床的平整度；而自动校正是一个更复杂的过程，不但包括校正热床的平整度，还包括调整三个
塔（Towers）的对称性，限位开关的高度，杆长等等，是一个相当复杂的过程。

#### Marlin 固件对于自动调平和自动校正的支持现状

Marlin 固件的碎片化越来越严重了！如果上 Github, 你会发现目前 Marlin 至少有 1800 多个 fork。最最正宗的
Marlin 固件是由 Erik 维护的。不幸的是，尽管已经存在了很久，但是目前对于 Deltabot 的自动调平支持的还
不是很好（原因嘛~也许 Marlin 固件要做到大而全，尽量支持各种结构和机型，当然不可能在短时间内将所有事
情都做完美）。

目前支持 Deltabot 自动调平的固件可以参考 Jcrocholl 的 Marlin 固件；而『支持』自动校正的是
RichCattell 的 Marlin 固件。

#### Jcrocholl 的 Marlin 代码
##### G29 和 G30
阅读 Marlin 的代码，可以发现控制 Deltabot 运动的全部代码几乎都在 Marlin_main.cpp 这个文件的
Process_commands() 文件里。通过 switch 语句来处理不同的 G-Code, M-Code 指令。在 Jcrocholl 版本的
Marlin 中，G30 的作用是探测某一点的 Z-高度。让我们来研究一下代码：

```c++
    case 30: // G30 Single Z Probe
        {
            engage_z_probe(); // Engage Z Servo endstop if available
			/* 这个函数是在 marlin_main.cpp 里面定义的，作用是放下Z-探测探针（当然有各种办法放下，比
			   如用『伺服电机』或者干脆让 Z-探针接触皮带从而放下探针）。崩溃的是，让 Z-探针接触皮带的
			   坐标是写死在固件里的（并没有提供设置参数），因此 Jcrocholl 的 Marlin 注定是高度定制化
		       的。
			*/
            st_synchronize();
			/* 这个函数的定义可以在 Stepper.cpp 这个文件里面找到，是直接控制步进电机用的。作用是完成
			   缓充区里暂存的命令，并负责管理热床的状态、更新 LCD 显示等等。
		    */

            // TODO: make sure the bed_level_rotation_matrix is identity or the planner will get set incorectly
            setup_for_endstop_move();
			/* 设定 feedrate 等等，但最重要的是 enable_endstops(true)，即把一个检测 endstop 状态的变
               量：check_endstops 的值设为 true。
		    */

            feedrate = homing_feedrate[Z_AXIS];

            run_z_probe();
			/* 这才是最重要的一句：开始 z-探测。这个函数也是 Jcrocholl 特有的，下面我们将分析这个函
			   数的功能。
			*/

            SERIAL_PROTOCOLPGM(MSG_BED);
            SERIAL_PROTOCOLPGM(" X: ");
            SERIAL_PROTOCOL(current_position[X_AXIS]);
            SERIAL_PROTOCOLPGM(" Y: ");
            SERIAL_PROTOCOL(current_position[Y_AXIS]);
            SERIAL_PROTOCOLPGM(" Z: ");
            SERIAL_PROTOCOL(current_position[Z_AXIS]);
            SERIAL_PROTOCOLPGM("\n");

            clean_up_after_endstop_move();
            retract_z_probe(); // Retract Z Servo endstop if available
        }
        break;

```
run_z_probe() 的代码：

```c++
static void run_z_probe() {
    plan_bed_level_matrix.set_to_identity();

#ifdef DELTA
    enable_endstops(true);
    float start_z = current_position[Z_AXIS];
	// 当前的打印头位置的 z 坐标

    long start_steps = st_get_position(Z_AXIS);
	/* 这句很奇怪，得到 Z-柱的步进电机当前的步数，但是对于 Deltabot 来说，Z-柱的步数和打印头的 Z-坐
	 标之间有直接关系吗？

	*/

    feedrate = homing_feedrate[Z_AXIS]/10; // 让移动速度是 Homing 速度的十分之一
    destination[Z_AXIS] = -10; // 设置打印头 z-坐标的预期值为 -10
    prepare_move_raw(); // 规划运动
    st_synchronize(); // 完成缓冲
    endstops_hit_on_purpose(); // 设置三个轴 hit 的值为 false

    enable_endstops(false); //设置 check_endstops 这个变量为 false
    long stop_steps = st_get_position(Z_AXIS);

    float mm = start_z - float(start_steps - stop_steps) / axis_steps_per_unit[Z_AXIS];
    current_position[Z_AXIS] = mm;
    calculate_delta(current_position);
    plan_set_position(delta[X_AXIS], delta[Y_AXIS], delta[Z_AXIS], current_position[E_AXIS]);
#else
    feedrate = homing_feedrate[Z_AXIS];

    // move down until you find the bed
    float zPosition = -10;
    plan_buffer_line(current_position[X_AXIS], current_position[Y_AXIS], zPosition, current_position[E_AXIS], feedrate/60, active_extruder);
    st_synchronize();

        // we have to let the planner know where we are right now as it is not where we said to go.
    zPosition = st_get_position_mm(Z_AXIS);
    plan_set_position(current_position[X_AXIS], current_position[Y_AXIS], zPosition, current_position[E_AXIS]);

    // move up the retract distance
    zPosition += home_retract_mm(Z_AXIS);
    plan_buffer_line(current_position[X_AXIS], current_position[Y_AXIS], zPosition, current_position[E_AXIS], feedrate/60, active_extruder);
    st_synchronize();

    // move back down slowly to find bed
    feedrate = homing_feedrate[Z_AXIS]/4;
    zPosition -= home_retract_mm(Z_AXIS) * 2;
    plan_buffer_line(current_position[X_AXIS], current_position[Y_AXIS], zPosition, current_position[E_AXIS], feedrate/60, active_extruder);
    st_synchronize();

    current_position[Z_AXIS] = st_get_position_mm(Z_AXIS);
    // make sure the planner knows where we are as it may be a bit different than we last said to move to
    plan_set_position(current_position[X_AXIS], current_position[Y_AXIS], current_position[Z_AXIS], current_position[E_AXIS]);
#endif
}

```

prepare_move_raw() 的代码，在 Marlin_main.cpp 里定义：

```c++
void prepare_move_raw()
{
  previous_millis_cmd = millis();
  // 这是一个 Arduino 内部函数，得到 Arduino 运行到现在的时间（是个
  // 无符号长整型），Arduino 将会在 50 天后重置时间

  calculate_delta(destination);
  // 输入打印头的笛卡尔坐标，得到打印头的 delta 坐标（三个滑车向下移动的距离）

  plan_buffer_line(delta[X_AXIS], delta[Y_AXIS], delta[Z_AXIS],
                   destination[E_AXIS], feedrate*feedmultiply/60/100.0,
                   active_extruder);
  // 将线性运动加入 buffer, x, y, z 是带符号的目标位置，单位是 mm

  for(int8_t i=0; i < NUM_AXIS; i++) {
    current_position[i] = destination[i];
  }
  // 将当前打印头位置位置设为目标位置，表明运动完成
}
```

以下是 RichCattell 的z_probe() 代码，在 Marlin_main.cpp 文件里定义：
```c++
float z_probe() {
  feedrate = AUTOCAL_TRAVELRATE * 60;
  prepare_move();
  st_synchronize();

  enable_endstops(true);
  float start_z = current_position[Z_AXIS];
  long start_steps = st_get_position(Z_AXIS);

  feedrate = AUTOCAL_PROBERATE * 60;
  destination[Z_AXIS] = -20;
  prepare_move_raw();
  st_synchronize();
  endstops_hit_on_purpose();

  enable_endstops(false);
  long stop_steps = st_get_position(Z_AXIS);

  //saved_position[X_AXIS] = float((st_get_position(X_AXIS)) / axis_steps_per_unit[X_AXIS]);
  //saved_position[Y_AXIS] = float((st_get_position(Y_AXIS)) / axis_steps_per_unit[Y_AXIS]);
  //saved_position[Z_AXIS] = float((st_get_position(Z_AXIS)) / axis_steps_per_unit[Z_AXIS]);

  float mm = start_z -
    float(start_steps - stop_steps) / axis_steps_per_unit[Z_AXIS];
  current_position[Z_AXIS] = mm;
  calculate_delta(current_position);
  plan_set_position(delta[X_AXIS], delta[Y_AXIS], delta[Z_AXIS],
		    current_position[E_AXIS]);

  for(int8_t i=0; i < 3; i++) {
    saved_position[i] = float(st_get_position(i) / axis_steps_per_unit[i]);
    }

  destination[Z_AXIS] = mm + AUTOCAL_PROBELIFT;
  prepare_move_raw();
  st_synchronize();
  return mm;
}
```

以下是 prepare_move() 的代码，在 Marlin_main.cpp 里定义：

```c++
void prepare_move()
{
  clamp_to_software_endstops(destination);

  previous_millis_cmd = millis();
#ifdef DELTA
  float difference[NUM_AXIS];
  for (int8_t i=0; i < NUM_AXIS; i++) {
    difference[i] = destination[i] - current_position[i];
  }
  float cartesian_mm = sqrt(sq(difference[X_AXIS]) +
                            sq(difference[Y_AXIS]) +
                            sq(difference[Z_AXIS]));
  if (cartesian_mm < 0.000001) { cartesian_mm = abs(difference[E_AXIS]); }
  if (cartesian_mm < 0.000001) { return; }
  float seconds = 6000 * cartesian_mm / feedrate / feedmultiply;
  int steps = max(1, int(DELTA_SEGMENTS_PER_SECOND * seconds));
  // SERIAL_ECHOPGM("mm="); SERIAL_ECHO(cartesian_mm);
  // SERIAL_ECHOPGM(" seconds="); SERIAL_ECHO(seconds);
  // SERIAL_ECHOPGM(" steps="); SERIAL_ECHOLN(steps);
  for (int s = 1; s <= steps; s++) {
    float fraction = float(s) / float(steps);
    for(int8_t i=0; i < NUM_AXIS; i++) {
      destination[i] = current_position[i] + difference[i] * fraction;
    }
    calculate_delta(destination);
    adjust_delta(destination);
    plan_buffer_line(delta[X_AXIS], delta[Y_AXIS], delta[Z_AXIS],
                     destination[E_AXIS], feedrate*feedmultiply/60/100.0,
                     active_extruder);
  }
#else

```
