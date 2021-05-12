# LiteXLoader - 文件系统 API

这里提供了脚本读写文件、操作目录以及一些系统调用相关的函数支持。

## 文件读写 API

> 注：所有文本相关的操作均使用UTF-8编码

### 读入文件的所有内容（文本格式）  
`fileReadAll(path)`
- 参数：
    1. path : `String`  
    目标文件的路径，相对路径以BDS根目录为基准  
- 返回值：文件的所有数据
- 返回值类型：`String` 
    - 如返回值为 `Null` 则表示读取失败  
<br>

### 清空指定文件的所有内容并写入（文本格式）  
`fileWriteAll(path,text)`
- 参数：
    1. path : `String`  
    目标文件的路径，相对路径以BDS根目录为基准  
    2. text : `String`  
    要写入的内容  
- 返回值：是否写入成功  
- 返回值类型：`Boolean`   
<br>

### 向指定文件追加一行（文本格式）  
`fileWriteLine(path,text)`
- 参数：
    1. path : `String`  
    目标文件的路径，相对路径以BDS根目录为基准  
    2. text : `String`  
    要写入的内容  
- 返回值：是否写入成功  
- 返回值类型：`Boolean`   
<br>

## 文件与目录 API

> 注：所有传入函数的相对路径都以BDS根目录为基准

### 创建文件夹  
`dirCreate(dir)`
- 参数：
    1. dir : `String`  
    目标文件夹的路径  
    可以直接创建多层，不需要逐层创建  
- 返回值：是否成功创建  
- 返回值类型：`Boolean`     
<br>

### 删除文件 / 文件夹  
`pathDelete(path)`
- 参数：
    1. path : `String`  
    目标文件 / 文件夹的路径  
- 返回值：是否成功删除  
- 返回值类型：`Boolean`   
<br>

### 判断文件 / 文件夹是否存在  
`pathExists(path)`
- 参数：
    1. path : `String`  
    目标文件 / 文件夹的路径  
- 返回值：目标是否存在  
- 返回值类型：`Boolean`   
<br>

### 判断文件 / 文件夹是否存在  
`pathExists(path)`
- 参数：
    1. path : `String`  
    目标文件 / 文件夹的路径  
- 返回值：目标是否存在  
- 返回值类型：`Boolean`   
<br>

### 复制文件 / 文件夹到指定位置  
`pathCopy(from,to)`
- 参数：
    1. from : `String`  
    源文件 / 文件夹的路径
    2. to : `String`  
    目标文件 / 文件夹的位置  
- 返回值：是否复制成功  
- 返回值类型：`Boolean`   
<br>

### 移动文件 / 文件夹到指定位置  
`pathCopy(from,to)`
- 参数：
    1. from : `String`  
    源文件 / 文件夹的路径
    2. to : `String`  
    目标文件 / 文件夹的位置  
- 返回值：是否复制成功  
- 返回值类型：`Boolean`   
<br>

### 重命名指定文件 / 文件夹  
`pathRename(from,to)`
- 参数：
    1. from : `String`  
    文件 / 文件夹的旧名字
    2. to : `String`  
    新名字  
- 返回值：是否复制成功  
- 返回值类型：`Boolean`   
<br>

## 系统调用 API

### 调用shell执行指定命令（注意！不是MC命令）  
`systemCmd(cmd[,callback,timeLimit])`
- 参数：
    1. cmd : `String`  
    执行的系统命令
    2. callback(可选参数) : `Function`  
    命令执行的进程结束之后返回数据使用的回调函数  
    默认为`Null`，即不执行回调函数
    3. timeLimit(可选参数) : `Number`  
    运行命令进程运行的最长时间，默认为`-1`，即无限长
- 返回值：是否成功启动命令  
- 返回值类型：`Boolean`   
<br>