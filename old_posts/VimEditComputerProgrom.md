---
title: Vim Edit Computer Program
date: "2019-05-12"
summary: "vim有许多辅助编写计算机程序的命令，可以编译一个进程并直接跳到报错的位置" 
---
vim有许多辅助编写计算机程序的命令，可以编译一个进程并直接跳到报错的位置。  

## 一、编译  
在vim内部可以编译程序并且跳转到出错的位置。  

在vim中输入以下命令，程序“make”将会被执行，结果会被捕获。  
`:make {arguments}`
在vim中会显示出错信息。此时按下`<Enter>`键，vim会显示对应的文件并跳转到出错的位置。  

下面是一些常用命令：
1. `:cnext`将跳转到下个出错位置，`:cprevious`将跳转到前个出错位置  
2. `:cc`将显示完整的出错信息  
3. `:clist`将显示完整的出错列表。
4. `:clist!`将显示所有的出错列表，包含链接错误等等  
5. `:cfirst`将跳到第一个出错位置，`clast`将跳到最后一个出错位置  
6. `:cc 3`将跳到第3个出错位置  

可以通过设置`makeprg`选项指定要运行的编译器,通过斜杠指定传递的参数，例如  
`:set makeprg=nmake\ -f\ project.mak`  

## 二、C风格的文本缩进
对于C或者C风格的程序例如Java或者C++，可以通过设置`cindent`选项来控制缩进。一般来说四个空格是合适的。  
`set cindent shiftwidth=4`  

可以通过`=`操作符来对齐缩进。最简单的命令是`==`，该命令会将当前行的缩进对齐。`=`操作符可以在可视化模式下使用。一个很有用的命令是`=a{`，这个命令会将当前`{}`所在的区域全部缩进对齐。  
