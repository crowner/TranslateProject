Linux：使用bash删除目录中的特定文件
================================================================================
![](http://s0.cyberciti.org/images/category/old/terminal.png)

我是一个Linux新手用户。现在我需要清理一个下载目录中的文件，其实我就是想删除～/Download/文件夹下面除了以下格式的文件外所以其它文件：
*.iso - 所有的iso格式的文件。
*.zip - 所有zip格式的文件。

我如何在一个基于Linux，OS X 或者Unix-like系统上的bash shell中删除特定的文件呢？

Bash shell 支持丰富的文件模式匹配符例如：

- * － 匹配所有的文件。
- ？ － 匹配文件名中的单个字母。
- [...] － 匹配封闭括号中的任何一个字母。

### 策略 #1: 见识一下扩展的模式匹配符 ###

这里你需要用系统内置的shopt命令来开启shell中的extglob选项，然后你就可以使用扩展的模式符了，这些模式匹配符如下：

1. ?(pattern-list) － 匹配零次或一次给定的模式。
1. *(pattern-list) －至少匹配零次给定的模式。
1. +(pattern-list) － 至少匹配一次给定的模式。
1. @(pattern-list) － 匹配一次给定的模式。
1. !(pattern-list) － 匹配所有除给定模式以外的模式。

一个模式列表就是一个或多个用 | 分开的模式（文件名）。首先打开extgolb选项：

    shopt -s extglob
 
#### 在Bash中删掉除*.zip和*.iso文件以外的所有文件 ####

rm 命令的语法格式为：

    ## 仅保留 file1 文件 ##
    rm  !(file1)
     
    ## 仅保留 file1 和 file2 文件## 
    rm  !(file1|file2)
     
    ## 仅保留 zip 文件 ##
    rm  !(*.zip)
     
    ## 仅保留 zip 和 iso 文件 ##
    rm  !(*.zip|*.iso)

    ## 你也可以使用完整的目录 ##
    rm /Users/vivek/!(*.zip|*.iso|*.mp3)
     
    ## 传递参数 ##
    rm [options]  !(*.zip|*.iso)
    rm -v  !(*.zip|*.iso)
    rm -f  !(*.zip|*.iso)
    rm -v -i  !(*.php)

最后，关闭 extglob 选项：

    shopt -u extglob
 
### 策略 #2: 使用bash的 GLOBIGNORE 变量删除指定文件以外的所有文件 ###

摘自 [bash(1)][1] 手册页:
> 一个用冒号分开的模式列表定义了被路径扩展忽略的文件的集合。如果一个文件同时与路径扩展模式和GLOBIGNORE中的模式匹配，那么它就从匹配列表中移除了。

要删除所有文件只保留 zip 和 iso 文件，应如下设置 GLOBIGNORE：

    ## 只在 BASH 中可行 ##
    cd ~/Downloads/
    GLOBIGNORE=*.zip:*.iso
    rm -v *
    unset GLOBIGNORE
 
### 策略 #3: 用 find 命令删除所有其它文件仅保留 zip 和 iso 文件 ###


如果你正在使用 tcsh/csh/sh/ksh 或者其它shell，你可以在Unix－like系统上试着用下面find命令的语法格式来删除文件：

    find /dir/ -type f -not -name 'PATTERN' -delete
 
或者

    ## 对于怪异的文件名可以使用 xargs ##
    find /dir/ -type f -not -name 'PATTERN' -print0 | xargs -0 -I {} rm {}
    find /dir/ -type f -not -name 'PATTERN' -print0 | xargs -0 -I {} rm [options] {}
 

为了删除 ～/source 目录下除 php 以外的文件，键入：

    find ~/sources/ -type f -not -name '*.php' -delete

或者

    find ~/sources/ -type f -not -name '*.php' -print0 | xargs -0 -I {} rm -v {}
 
只保留 *.zip 和 *.iso 文件的语法如下：

    find . -type f -not \( -name '*zip' -or -name '*iso' \) -delete
 

更多信息参见[bash command man page][1]和[find command man page][2]。

--------------------------------------------------------------------------------

via: http://www.cyberciti.biz/faq/linux-bash-delete-all-files-in-directory-except-few/

译者：[Linchenguang](https://github.com/Linchenguang) 校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创翻译，[Linux中国](http://linux.cn/) 荣誉推出

[1]:http://www.manpager.com/linux/man1/bash.1.html
[2]:http://www.manpager.com/linux/man1/find.1.html