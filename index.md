
# 命令行入门

©knifefire著，转载记得注明出处哦！

#### 注：程序员不学命令行，不如回家卖烤肠

## 学前基础

### 文件（夹）即目录
    ~：用户目录
    /：Linux没有盘符的概念，/就是硬盘
    .：当前目录
    ..：父级目录
    $：没有实际意义，仅表示可以输入命令

### 从背单词开始

    directory 目录、文件夹
    file 文件
    make 新建
    remove 删除
    move 移动
    copy 复制
    list 罗列
    link 链接
    find 查找
    echo 发出回声、重复
    touch 触摸
    change 改变

### 缩写

    创建目录---make directory---mkdir
    删除---remove---rm
    移动/重命名---move---mv
    复制---copy---cp
   罗列---list---ls
   改变目录---change directory---cd

### 小试牛刀

    cd ~/Desktop 进入桌面目录
    mkdir demo 创建 demo 目录，看看桌面，闪现
    cd demo 进入 demo 目录
    touch 1.txt 创建 1.txt 文件
    mv 1.txt 2.txt 将 1.txt 重命名为 2.txt
    rm 2.txt 删除 2.txt

### 绝对路径与相对路径

前者相当于上海市南京东路100号，

后者相当于上海市南京东路100号的隔壁

一个可以直接找到，另一个必须通过相对于它的地址才能找到

一般以 / 开头的路径就是绝对路径，如 /Users/Tom、/c/Users/

### 常见的自带命令

#### 目录
    
    进入目录 ----- cd

小技巧：在任何目录下输入：cd回车，都可以回到 ~ 目录

    显示当前目录（绝对地址）----- pwd
    创建目录 ----- mkdir 目录名
    创建多级目录 ----- mkdir -p "父级目录/子级目录"
    创建多个目录 ----- mkdir -p 目录1 目录2
    我是谁（查看系统管理员名称） ----- whoami

#### 路径

    查看路径（展开当前目录下的内容） ----- ls
    查看所有路径（所有内容，包括以 . 开头的隐藏内容） ----- ls -a
    查看路径信息（d:目录；-:文件；r:可读；w:可写；x:可执行）----- ls -l
    查看所有路径信息 ------ ls -al

#### 文件

    创建文件 ----- touch 文件名
    改变文件更新时间 ----- touch 文件名
    写入内容到文件（文件不存在那么就创建文件并写入；会覆盖）----- echo '内容' > 文件路径
    追加文件内容 ----- echo '内容' >> 文件路径 （win 不支持）

#### 复制

    复制文件（内容） ----- cp 源路径 目标路径
    复制目录 ----- cp -r 源路径 目标路径

#### 移动

    移动/重命名文件、目录 ----- mv 源路径 目标路径

#### 删除

    删除文件 ----- rm 文件名
    强制删除文件（不会询问确认） ----- rm -f 文件名
    删除目录（递归删除） ----- rm -r 目录名
    强制删除目录 ----- rm -rf 目录名

#### 其他

    用默认编辑器打开文件 ----- open（非 win 用户）/ start（win 用户）
    查看目录结构 ----- tree （win 不支持）
    查看文件内容 ----- cat 文件名
    下载文件到本地文件 ----- curl -L https://www.baidu.com > baidu.html
    拷贝网页 ----- wget -p -H -e robots=off https://www.baidu.com （win 不支持）
    磁盘占用 ----- df -kh
    当前文件大小 ----- du -sh
    各文件大小 ----- du -h
    使用 vim 打开文件 ----- vi 文件名

### 如何退出 vim

(不保存）强制退出：狂按 ESC ，输入:q!回车

(保存）退出：狂按 ESC ，输入:wq回车

q：quit；w：write；

为什么要狂按：防止手欠没按上

#### 怎么学习 vim

vim 被誉为编辑器之神，不知道编辑器与 IDE 区别请自行 google

如果你想要入门 vim ：

在命令行输入 vimtutor，即可看完官方自带中文教程，看完它

简明 vim 练级教程

一个 vim 游戏

#### 快捷键

    方向键上/下 ----- 上一条命令/下一条命令
    Tab ----- 自动补全路径
    '>' ----- 重定向
    && ----- 前面命令执行成功了，后面命令才执行
    || ----- 前面命令执行失败了，后面命令就执行
    ; ----- 前面命令不管执行是否成功，只要执行完了就执行后面命令

### 关于 ~/.bashrc 文件的奇淫技巧

~/.bashrc 文件功能异常强大，谁用谁知道

#### 自动运行

命令行输入 start ~/.bashrc，编辑这个文件，内容为 echo 'Hi'

当然，你也可以直接命令行 echo "echo 'Hi'" >> ~/.bashrc

保存、关闭 git bash，重新打开 git bash，是不是看见了Hi

这说明每次进入 git bash，都会优先执行 ~/.bashrc 里面的命令

那么能利用这个做什么呢？重新编辑 ~/.bashrc ，将刚才编辑的命令改为 cd ~/Desktop，重启 git bash，有没有发现默认进入桌面目录？

你可以利用 ~/.bashrc 文件在进入 git bash 前执行任何命令，是不是很方便？
alias

在 ~/.bashrc 里新增一行 alias hw="echo 'Hello World!'"，不要自己在等号两边加空格，保存退出

命令行输入 source ~/.bash_profile ，作用是执行 ~/.bashrc 而不需要重启 git bash

命令行输入 hw，就会看到 Hello World!

这说明 hw 被设置成了 Hello World! 的缩写

利用这个我们可以将很多命令进行缩写设置，比如

    alias ll="ls -l"
    alias la="ls -a"
    alias rr="rm -rf"
    alias cdd="cd ~/Desktop"
    alias gst="git status -sb"
    alias ga="git add"
    alias ga.="git add ."
    alias gc="git commit"
    alias gc.="git commit ."

保存退出，命令行输入 source ~/.bash_profile

这样你的日常和Git操作就会简单很多

    ga 1.txt
    ga .
    gc 1.txt
    gc .
    gst

### 环境变量

你还可以在 ~/.bashrc 里面设置一些环境变量，比如加一行

export SASS_BINARY_SITE="http://npm.taobao.org/mirrors/node-sass"

那么你安装 node-sass 的时候就不会因为被墙而报错

### 设置PATH

~/.bashrc 文件加一条 export PATH="目录的绝对路径:$PATH"

具体会有什么效果可以看脚本，里面有解释

好啦，当你大致地过了一遍上面的知识，你就可以愉快地开始你的命令行之旅了，祝你旅途愉快!!!

[大家可以看看我写的另一篇文章，关于termux的](http://jason-hue.github.io/termux/)

©knifefire & ZH
