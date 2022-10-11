# Shell 脚本语言笔记

# oh-my-zsh 国内安装源

- 安装zsh 解释器

`apt-get install zsh -y`

- curl 安装方法调用的国内的gitee仓库

`sh -c "$(curl -fsSL https://gitee.com/pocmon/ohmyzsh/raw/master/tools/install.sh)"`

- wget 安装方法

`sh -c "$(wget -O- https://gitee.com/pocmon/ohmyzsh/raw/master/tools/install.sh)"`

# 配置 cp命令和mv命令 复制或者移动文件时显示进度条

> 由于cp 和 mv命令都属于coreutils工具包下，因此我们的主要操作就是在编译coreutils的收加入补丁从而实现进度条功能

```bash
# 下载coreutils
wget http://ftp.gnu.org/gnu/coreutils/coreutils-8.32.tar.xz
tar -xJf coreutils-8.32.tar.xz
cd coreutils-8.32/
# 下载 github 上的补丁
wget https://raw.githubusercontent.com/jarun/advcpmv/master/advcpmv-0.8-8.32.patch
# 打补丁，实现进度条显示
patch -p1 -i advcpmv-0.8-8.32.patch
patching file src/copy.c
patching file src/copy.h
patching file src/cp.c
patching file src/mv.c
# 编译安装
./configure
make
# 将打补丁生成的cp和mv命令的二进制文件复制到bin目录下
sudo cp src/cp /usr/local/bin/cp
sudo cp src/mv /usr/local/bin/mv
# 如何使用
# 在使用cp和mv命令的时候加上 -g 参数就可以显示进度条了， 为了方便可以在.bashrc 文件中设置alias

alias cp='cp -ig'
alias mv='mv -ig'

# 让刚才添加的内容生效
source .bashrc
```

# 推荐一个 Linux crontab 定时任务、定时器 可视化在线工具

![image](https://user-images.githubusercontent.com/65467296/180168222-d9a731dd-895e-4d2f-88c2-58ecff1d1091.png)

[crontab](https://toolhut.cn/tools/crontab)
