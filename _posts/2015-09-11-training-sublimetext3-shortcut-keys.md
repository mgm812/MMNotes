---


layout:     post
title:      Sublime Text 3 常用快捷键
category:   training
tag:        sublime

---

终于下决定从TextMate转到SublimeText，为了快速的上手SublimeText3，我计划从学习SublimeMate3的快捷键开始，打算收录常用的快捷键，复杂的使用方式用gif图片来演示，并会持续更新这篇文章。欢迎路过的大侠们留言提供我遗漏的快捷键，由于一直使用Mac系统，我就先从Mac版收录啦，Windows的兄弟们，会单独找时间来更新。希望这篇文章能成为收录SublimeText3快捷键最全的文章。

## Mac版

### 快捷键缩写说明

首先对即将使用的按键缩写做一个统一说明：

| 缩写	| 全称    
| ---	| ---	
| cmd	| command
| opt 	| option
| ctrl	| control
| shift	| shift
| up    | 向上箭头键
| down  | 向下箭头键
| left  | 向左箭头键
| right | 向右箭头键
| del 	| delete

### 文件操作

以下是`文件菜单`下常用的快捷键操作：

| 快捷键组合			| 说明
| --------			| ---
| cmd + o 			| 快速打开文件夹
| cmd + w			| 关闭当前页
| cmd + n 			| 打开新分页
| cmd + shift + t 	| 重新打开刚关闭的分页

### 编辑操作

| 快捷键组合				| 说明
| --------				| ---
| cmd + y				| 复制刚输入的字符串，按几次复制几次
| cmd + shift + v 		| 带格式的复制
| cmd + ]				| 缩进
| cmd + [				| 取消缩进
| cmd + ctrl + up		| 当前行或选中的内容往上移
| cmd + ctrl + down		| 当前行或选中的内容往下移
| cmd + shift + d 		| 复制当前行或选中的内容
| cmd + j				| 合并2行
| cmd + /				| 注释或取消注释一行
| cmd + opt + /			| 注释或取消注释一块选中的区域
| cmd + enter			| 往后面插入一行
| cmd + shift + enter	| 往前面插入一行
| cmd + del 			| 删除到当前行开始
| ctrl + k 				| 删除到当前行的末尾
| ctrl + shift + k 		| 删除当前行或选中的内容
| cmd + ctrl + [		| 折叠当前区域的代码
| cmd + ctrl + ] 		| 展开当前区域的代码
| cmd + k then u 		| 全部大写
| cmd + k then l 		| 全部小写
| f5 					| 排序
| ctrl + f5 			| 大小写敏感排序

### 选择操作

#### cmd + shift + l

对选中的区域做多行编辑时，使用此快捷键可以快速的打散进行多行编辑，特别是批量添加`"`和`,`：
![cmd+shift+l](http://mmy812.github.io/MMResources/sublime3/sublime3-sk-cmd+shift+l.gif)

#### cmd + l

选中当前行，多次连续操作，会依次选中下一行：
![cmd+l](http://mmy812.github.io/MMResources/sublime3/sublime3-sk-cmd+l.gif)

#### cmd + d

`cmd + d`选择当前光标所在的词并高亮该词所有出现的位置，再次`cmd + d`选择该词出现的下一个位置，在多重选词的过程中，使用`cmd + k`进行跳过，使用`cmd + u`进行回退，使用Esc退出多重编辑。
![cmd+d](http://mmy812.github.io/MMResources/sublime3/sublime3-sk-cmd+d-cmd+k-cmd+u.gif)

#### ctrl + shift + m

选中当前光标所处的`()`，`[]`，`{}`区域，多次操作，会依次选中上一层的区域：
![ctrl+shift+m](http://mmy812.github.io/MMResources/sublime3/sublime3-sk-ctrl+shift+m.gif)

#### cmd + shift + j

选中当前光标所处的缩进区域，多次操作，会依次选中上一级缩进的区域：
![cmd+shift+j](http://mmy812.github.io/MMResources/sublime3/sublime3-sk-cmd+shift+j.gif)

#### cmd + shift + a

选中当前光标所处的标签包裹区域，多次操作，会依次选中上一级标签包裹区域：
![cmd+shift+a](http://mmy812.github.io/MMResources/sublime3/sublime3-sk-cmd+shift+a.gif)

