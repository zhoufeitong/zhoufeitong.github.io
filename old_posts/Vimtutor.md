---
title: Vim Tutor
date: "2019-04-14"
summary: "虽然一直在使用vim编辑器，但其实一直没有练习过。借着ARTS中T的名头，就稍微学习一下vimtutor并将其中的总结放在这" 
---
虽然一直在使用vim编辑器，但其实一直没有练习过。借着ARTS中T的名头，就稍微学习一下vimtutor并将其中的总结放在这。  

## 一
1. 使用h，j，k，l作为vim中光标的移动键(比上下左右要有效率的多)。  
2. 使用:q!(`quit!`)强制退出当前正在编辑的文件  
3. 使用x删除当前光标停留处的文字  
4. 使用i(`insert`)在当前光标位置处插入内容  
5. 使用A(`Append`)在当前最后一行处添加内容  

## 二
1. 使用dw(`delete word`)来删除当前光标处的一个单词  
2. 使用d$删除当前位置到行末的所有内容  
3. 许多改变文本的命令都由一个`operator`和`motion`组成，例如d代表删除`operator`，而`motion`可以有如下选择：  
    * w：直到下一个单词的起始位置，不包括该起始位置  
    * e: 直到当前单词的结束位置，包括该结束位置  
    * $: 直到当前行的结尾，包括最后一个单词  
    如果只按上述`motion`则可以让光标按`motion`移动  
4. 在`motion`前面可以使用数字进行对多个`motion`的操作  
5. 使用0到一行的起始位置处  
6. 使用dd删除一整行数据  
7. 使用u来撤销上一个操作，U来修复一整行的操作，CTRL-R来撤销撤销操作  

## 三
1. 使用p(`put`或`paste`)来放置vim寄存器中的文本数据(可通过dd，d，yy等操作得到)  
2. 使用r(`replace`)来替换当前光标处的文本  
3. 使用c(`change`)+`motion`来改变文版，注意按c之后会进入插入模式  

## 四
1. 使用CTRL-G命令显示当前文件名以及总行数、当前行数  
2. 使用G(`Go`)到当前文件底端，gg到当前文件顶端,[number]G到[number]行  
3. 使用/[text]搜索和[text]一样的文本，n是前进，N是后退  
4. 使用%来匹配各种括号  
5. 使用:s(`substitute`)来替进行各种替换  

## 五
1. 使用:!来执行外部的shell命令，例如:!ls就可以列举目录  
2. 使用:w(`write`) FILENAME来将当前已经写完的内容写入某个文件  
3. 使用v(`visual`)进入可视化模式，选择部分内容并利用:w来将这些内容写入某个文件  
4. 使用:r(`read`) FILENAME来将目标文件的内容读入当前正在编辑的文件中(不一定是文件内容，某个命令的输出也可以，感觉和管道或是重定向很像)  

## 六
1. 使用o来在当前行下面插入一行，使用O来在当前行上面插入一行  
2. 使用a来在当前光标的下一个位置插入文本  
3. 使用R来批量替换文本  
4. 使用y来复制，p来粘贴。  

## 总结  
对我来说，这个教程比较有用的是2.3,4.4和5.5。以后还要多多练习，对这些基本操作更加熟练