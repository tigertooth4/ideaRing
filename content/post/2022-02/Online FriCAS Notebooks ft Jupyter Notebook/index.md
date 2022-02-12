---
title: Online FriCAS Notebooks (ft. Jupyter Notebook)
date: '2022-1-28T10:07:00+08:00'
draft: false
tags: ["Math", "CAS", "FriCAS", "Online", "Remote", "日精一技"]

---

# 1. Remote Computation Service

I selected ~~Ubuntu~~ Debian Linux (Debian 11, the latest Debian Linux supported by the AliYun). The reason for selecting Debian over Ubuntu is the support for FriCAS is only available on Ubuntu 21.4, but Ubuntu 21.4 is not supported by AliYun for now.

 Here’s the instruction to run jFriCAS on Ubuntu. 

[](https://jfricas.readthedocs.io/_/downloads/en/latest/pdf/)

I’ve changed to AliYun afterwards, here’s the AliYun application info.

【阿里云】尊敬的tgth4用户：您的云服务器ECS创建成功（实例名称：iZ2ze5eib0jy8hmapmhbg2Z，公网IP：101.200.150.204）。系统用户名： root；若您忘记或未设置密码可进入ECS控制台-实例列表-重置密码。如您购买了数据盘请在实例创建后手动磁盘格式化分区，更多信息请查看站内信或邮件。

# 2. Installation Steps

## 2.1 Install jFriCAS and Jupyter

- Install Python3
  
    ```bash
    sudo apt install python3
    ```
    
- Install Pip3
  
    ```bash
    sudo apt install python3-pip
    ```
    
- Install ASDF
  
    ```bash
    sudo apt install cl-asdf
    ```
    
- Install Hunchentoot Webserver
  
    ```bash
    sudo apt install cl-hunchentoot
    ```
    
- Install Jupyter
  
    ```bash
    sudo apt install jupyter
    ```
    
- Install jFriCAS from PyPI
  
    ```bash
    pip3 install jfricas
    ```
    
- ~~Install FriCAS~~  I have noticed the installation must be done by compile from the source. Since the available Debian build was not based on sbcl.
  
    ```bash
    ~~apt install fricas~~
    ```
    
- Customize Jupyter notebook. See the following page for detail.
  
    [Customize your Jupyter Notebook Theme in 2 lines of code](https://link.medium.com/8LlqPwAswnb)
    
    ```bash
    pip3 install jupyterthemes
    ```
    
    I found the following  creates some satisfied result: 
    
    ```bash
    !jt -t solarizedl -f firacode -fs 9 -tf georgiaserif -tfs 11 -mathfs 100 -T -N -kl
    ```
    

## 2.2 Add New Sudoer

- First, we have to add a new user to the linux system
  
    ```bash
    adduser lxj
    ```
    
- Add user to the sudoer group
  
    ```bash
    usermod -aG sudo lxj
    ```
    
- Verify the user groups
  
    ```bash
    groups lxj
    ```
    
- Verify the sudo access
  
    ```bash
    su - lxj
    ```
    

## 2.3 Compile FriCAS from source

- Install git tools
  
    ```bash
    apt install git
    ```
    
- git pull the FriCAS source file in lxj’s directory (not in root’s home)
  
    ```bash
    git clone --depth 1 https://github.com/fricas/fricas.git
    ```
    
    In my case, the git clone command failed. So I just use wget with the source link of FriCAS 1.3.7-full.tar.bz2. And extract the file with 
    
    ```bash
    tar -xf ./fricas-1.3.7-full.tar.bz2
    ```
    
- Install libx11 libs, xvfb, gimp-dev tool, texlive, dvipng, Sphinx
  
    ```bash
    sudo apt install libx11-dev libxt-dev libice-dev \
                     libsm-dev libxau-dev libxdmcp-dev libxpm-dev
    sudo apt install xvfb
    sudo apt install libgmp-dev
    sudo apt install texlive dvipng
    pip3 install -U Sphinx
    ```
    
- Make a directory called fr-build, and build fricas into that directory, install it in `/usr/local/`
  
    ```bash
    mkdir fr-build
    cd fr-build
    ../fricas-1.3.7/configure --with-lisp="sbcl" --enable-gmp
    make && sudo make install
    ```
    

# 3. Running Jupyter Remotely As a Service

This part will  configure the Jupyter Environment for Remote Access

- Generate Jupyter configuration file in the newuser account’s home directory
  
    ```bash
    jupyter notebook --generate-config
    ```
    
- Add new user password to the notebook
  
    ```bash
    jupyter notebook password
    ```
    
- Edit the configuration file for remote access
  
    ```bash
    vim ~/.jupyter/jupyter_notebook_config.py
    ```
    
    Input the following contents in the beginning of the file
    
    ```bash
    c.NotebookApp.ip='*' # 代表任意ip是都可以访问jupyter
    c.NotebookApp.notebook_dir='/home/lxj/jupyter' # notebook的工作目录，可以自己的实际情况修改，注意要确保目录存在
    c.NotebookApp.open_browser = False # 不打开浏览器
    c.NotebookApp.port =8888  #可自行指定一个端口, 访问时使用该端口
    ```
    
- Configure firewall rules for port accessing in your server side, then type (according to the following [link](https://groups.google.com/g/fricas-devel/c/YPi7XGyCekY/m/Uz0Wg9o4BgAJ))
  
    ```bash
    SBCL_HOME=/usr/lib/sbcl/ nohup jupyter notebook > jupyter.log 2>&1 &
    ```
    
    to run jupyter notebook no hang up.  And finally you can run jupyter remotely.
    

# 4. Setup Pseudo-differential Operator Computation Environment

- `**scp**` ORESUS library to the server. I put the spad file in the jupyter directory under my home.
  
    ```bash
    scp ./ORESUS-patched.spad lxj@xxx.xxx.xxx.xxx:/home/lxj/jupyter
    ```
    
- Open this [Kuperschmidt deformation notebook](http://101.200.150.204:8888/notebooks/jfricas/Kuperschmidt-Deformation.ipynb) to try 😄

# References

- Here’s the official page for deploying jupyter notebook
  
    [Running a notebook server - Jupyter Notebook 6.4.8 documentation](https://jupyter-notebook.readthedocs.io/en/stable/public_server.html)