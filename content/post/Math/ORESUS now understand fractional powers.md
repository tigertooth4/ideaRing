---
title: "斜洛朗级数环的软件包现在可以计算一个算子的分数次方了！"
date: "2014-07-26 18:00:00"
draft: false
Tags: ["Math", "FriCAS", "Coding", "PDO", "ORESUS"]
author: "tt4"
---

先上张代码的图吧！![][image-1]

**FriCAS** 虽然是从 **AXIOM** 这门古董级语言中 fork 出来的一个分支，目前仍处在活跃开发期，但是很多功能仍然缺失，尤其是：调试的功能基！本！没！有！

有些时候，这门语言很灵活，例如：变量没有声明类型也可以使用；有些时候又严格得要命，例如：函数的参数必须是指定类型，你一个函数，
以 `Expression(Integer)` 为参数，给它传个 `Integer` 类型的变量，就不认了！必须要先转换成 `Expression(Integer)` 才可以。
所以，写个程序非常蛋疼。。。

编写程序的时候出了不少问题，错误信息有时候非常令人迷惑，例如：

* 这个错误信息：

	> Error detected within library code: (1 . failed) cannot be coerced to mode (Expression (Integer))  

不是说你传递的参数类型有问题，而八成是你的代码中对类型的处理不够谨慎：例如 `Ring` 中的 `exquo` 运算
（消去运算），会返回一个 `Union` 类型的变量：要么成功了，得到这个环中的元素，要么失败了，返回一个
字符串 `“failed”`。所以，不要以为消去一下，就直接可以用了，还要顾及到有可能返回的是字符串，这时候
需要这样：

```Haskell
    (a exquo b) case "failed" => "failed"
```

表示直接返回字符串 `“failed”`. 或者，

```Haskell
	(a exquo b) case "failed" => error "Through some error message..."
```

哦，会报这个错误的另一个原因就是这个 `exquo` 函数，在命令行中你可以写

```Haskell
	exquo(a,b)
```

但在 `spad` 文件中却不行，必须要写成二元运算的样子

```Haskell
	(a exquo b)
```

* 这样的错误：

	> \*\*\*\*\*\*\*\* Spad syntax error detected \*\*\*\*\*\*\*\*
	> Expected: BACKTAB
	> The prior line was:
	> 129\>             "^":(%,I) -> Union(%, "failed")
	> The current line is:
	> 136\>             fracStream (%, R, I, NNI, %) -\> SC

出错原因，一定是你 129 附近的哪行类型处理不当，或者少写括号了等等。了如，我在这里犯下的错误就是 `fracStream` 后面少了冒号

* 最后，貌似一切的错误，类型转换都已经处理到了，但是还是不行，一运行就死在那了，原因是：我在 delay 里用了这样的递归调用：假设

```Haskell
	foo: (param1,...) -> Stream(R)
```

在函数体里面，用了延迟运算和递归：

```Haskell
	delay
		concat(foo(param1,...),b)
```

这里的问题是：每次函数被调用的时候，都会先去运行 `foo`,然后在 `foo` 返回 `Stream(R)` 类型的值后，再和元素 `b` 合并。可是 `foo` 并没有终止条件，每次先运行 `foo`, 就算已经用延迟计算 `delay` 了，也会陷入无休止的循环。正确的做法（我不知道为什么这样），只要把 `b` 放前面就行了 （囧）。。。

好吧！无论如何经过两天的努力，耐心的在命令行里逐步运行代码，所有的错误都已经基本解决了。当然还有一些细节需要处理，但总算是迈出了里程碑式的一步！

[image-1]:	/Math/_images/fraction.png
