# javascript-code-segment

## md 语法与快捷键介绍：

1. 标题
   
   用#号表示

2. 字体加粗

    用**包裹起来

3. 斜体字

    用*包裹起来

4. 加粗加斜体

    用***包裹起来

5. 引用

    用>表示引用说明

6. 代码块

    用tab或者4个空格缩进表示, 也可以通过```将代码包裹起来表示代码块

7.  有序列表

    通过-加一个空格表示，后面跟内容

8.  无序列表

    通过数字加一个.以及一个空格表示，后面跟内容

## git使用场景总结

1. 假如本地有两个分支，a和b。在b分支开发新功能，每次开发一部分就合并到a分支上。此时合并的a分支有个问题，而b分支才完成一部分功能，不想提交。
   
方案：将b分支的修改暂存，切换到a分支工作，然后切换到b分支，恢复暂存继续开发。

首先在b分支执行
    
```
git stash
```

做完事之后，切换到b分支，执行

```
git stash pop
 ```

2. 分支创建与合并

```
git branch 分支名 // 创建一个新的分支
git checkout 分支名 // 切换分支
git push origin 分支名 // 新建的分支push到远端
```

3. 分支修改与合并

分支提交

```
git add 文件名 // 把修改的文件提交到暂存区
git commit -m '填写你提交的日志' // 把暂存区的内容提交到仓库
```

分支撤销

```
git reset HEAD 文件名 // 撤销添加到暂存区的文件
```

分支合并

```
git checkout 分支名a
git merge 分支名b
```

4. 回退到某次提交

```
git log
git reset --hard 提交标记
```

回退版本，之后的所有提交内容将被清除掉

5. 重返未来

```
git reflog
git reset -- hard 提交标记
```

## doc 目录

1. array篇（一）
2. array篇（二）
3. array篇（三）

## 问题集

1. no similarly named formulae found.

    发现找不到应有的包，重新安装一次homebrew-core，完美解决

    cd /usr/local/Homebrew/Library/Taps/homebrew/ rm -rf homebrew-core
    git clone https://github.com/Homebrew/homebrew-core.git

2. 使用gitstats

    git clone git://github.com/hoxu/gitstats.git
    cd gitstats
    ./gitstats 你的项目的位置 生成统计的文件夹位置

3. 安装gnuplot画图程序

    brew install gnuplot

4. mac终端下安装brew

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

    校验是否安装成功

    brew --version

