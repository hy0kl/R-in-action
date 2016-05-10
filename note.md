# R语言实战

## 第一章 入门

- R使用 `<-`,而不是传统的 `=` 作为赋值符号。
- 注释由符号 # 开头。

### 获取帮助

函数 | 功能
---- | ---
help.start() | 打开帮助文档首页
help("foo")或?foo | 查看函数foo的帮助(引号可以省略)
help.search("foo")或??foo | 以foo为关键词搜索本地帮助文档 
example("foo") | 函数foo的使用示例(引号可以省略)
RSiteSearch("foo") | 以foo为关键词搜索在线文档和邮件列表存档
apropos("foo", mode="function") | 列出名称中含有foo的所有可用函数
data() | 列出当前已加载包中所含的所有可用示例数据集
vignette() | 列出当前已安装包中所有可用的vignette文档 
vignette("foo") | 为主题foo显示指定的vignette文档

### 工作空间

用于管理R工作空间的函数

函数 | 功能
---- | ---
getwd() | 显示当前的工作目录
setwd("`mydirectory`") | 修改当前的工作目录为*mydirectory*
ls() | 列出当前工作空间中的对象
rm(objectlist) | 移除(删除)一个或多个对象
help(options) | 显示可用选项的说明
options() | 显示或设置当前选项
history(#) | 显示最近使用过的#个命令(默认值为25)
savehistory("myfile") | 保存命令历史到文件myfile中(默认值为.Rhistory)
loadhistory("myfile") | 载入一个命令历史文件(默认值为.Rhistory)
save.image("myfile") | 保存工作空间到文件myfile中(默认值为.RData)
save(objectlist, file="myfile") | 保存指定对象到一个文件中
load("myfile") | 读取一个工作空间到当前会话中(默认值为.RData)
q() | 退出R。将会询问你是否保存工作空间

### 输入和输出

1. 输入 函数source("filename")可在当前会话中执行一个脚本。
2. 文本输出 函数`sink`("filename")将输出重定向到文件filename中。默认情况下,如果文件已经存 在,则它的内容将被覆盖。使用参数`append=TRUE`可以将文本追加到文件后,而不是覆盖它。 参数`split=TRUE`可将输出同时发送到屏幕和输出文件中。不加参数调用命令sink()将仅向屏幕 返回输出结果。
3. 图形输出

函数 | 输出
--- | ---
pdf("filename.pdf") | PDF文件
win.metafile("filename.wmf") | Windows图元文件
png("filename.png") | PNG文件
jpeg("filename.jpg") | JPEG文件
bmp("filename.bmp") | BMP文件
postscript("filename.ps") | PostScript文件

最后使用dev.off()将输出返回到终端。

### 包

包是R函数、数据、预编译代码以一种定义完善的格式组成的集合。计算机上存储包的目录 称为库(library)。函数.libPaths()能够显示库所在的位置, 函数library()则可以显示库中 有哪些包。

R自带了一系列默认包(包括base、datasets、utils、grDevices、graphics、stats 以及methods),它们提供了种类繁多的默认函数和数据集。其他包可通过下载来进行安装。安装 好以后,它们必须被载入到会话中才能使用。命令search()可以告诉你哪些包已加载并可使用。

#### 包的安装

- install.packages()
- update.packages()
- installed.packages()

#### 包的载入

- library()

### 批处理

R CMD BATCH options infile outfile

## 第二章 创建数据集

### 数据集的概念

不同的行业对于数据集的行和列叫法不同。统计学家称它们为观测(observation)和变量 (variable),数据库分析师则称其为记录(record)和字段(field),数据挖掘/机器学习学科的研究者则把它们叫做示例(example)和属性(attribute)。

### 数据结构

R拥有许多用于存储数据的对象类型,包括标量、向量、矩阵、数组、数据框和列表。

#### 向量
向量是用于存储数值型、字符型或逻辑型数据的一维数组。执行组合功能的函数c()可用来创建向量。

*注意,单个向量中的数据必 须拥有相同的类型或模式(数值型、字符型或逻辑型)。标量是只含一个元素的向量。*