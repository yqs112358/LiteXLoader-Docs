# LiteXLoader - 系统功能接口文档

[<< 返回目录](README.md)

下列这些内容，为脚本插件提供了对接**底层系统功能**的接口，包括操作文件系统、访问网络等。  
这对脚本插件开发是重要的扩展，实现了高层对底层机制的直接互通。

<br>

## 获取系统信息 API

下面这些API提供了获取必要的系统信息的接口

### 获取当前时间字符串  

`system.getTimeStr()`

- 返回值：当前的时间字符串，使用当地时区和24小时制。  
  形如`2021-04-03 19:15:01`
- 返回值类型：`String`

<br>

### 获取当前的时间对象

`system.getTimeObj()`

- 返回值：当前的时间对象（`Object`）

- 返回值类型： `Object<Integer,Integer,Integer,Integer,Integer,Integer,Integer>`

  - 对于返回的某个时间对象tm，有如下这些成员：

  | 成员  | 含义                 | 类型      |
  | ----- | -------------------- | --------- |
  | tm.Y  | 年份数值（4位）      | `Integer` |
  | tm.M  | 月份数值             | `Integer` |
  | tm.D  | 天数数值             | `Integer` |
  | tm.h  | 小时数值（24小时制） | `Integer` |
  | tm.m  | 分钟数值             | `Integer` |
  | tm.s  | 秒数值               | `Integer` |
  | tm.ms | 毫秒数值             | `Integer` |

<br>

### 随机生成一个 GUID  字符串

`system.randomGuid()` 

- 返回值：一个随机生成的唯一标识符GUID
- 返回值类型： `String`

<br>

------

## 文件读写 API

下面这些API提供了脚本读写文件的接口

> 注：所有文本相关的操作均使用UTF-8编码。  

### 读入文件的所有内容

`file.read(path)`

- 参数：
  - path : `String`  
    目标文件的路径，相对路径以BDS根目录为基准
- 返回值：文件的所有数据
- 返回值类型：`String`
  - 如返回值为 `Null` 则表示读取失败

<br>

### 向指定文件写入内容

`file.write(path,text)`

- 参数：
  - path : `String`  
    目标文件的路径，相对路径以BDS根目录为基准

  - text : `String`  
    要写入的内容

- 返回值：是否写入成功

- 返回值类型：`Boolean`

> 注：若文件不存在会自动创建，若存在则会先将其**清空**再写入

<br>

### 向指定文件追加一行

`file.writeLine(path,text)`

- 参数：
  - path : `String`  
    目标文件的路径，相对路径以BDS根目录为基准

  - text : `String`  
    要写入的内容
- 返回值：是否写入成功
- 返回值类型：`Boolean`

<br>

------

## 文件与目录 API

下面这些API提供了操作文件、目录等与文件系统互动的接口

> 注：所有传入函数的相对路径都以BDS根目录为基准。  

### 创建文件夹  

`file.createDir(dir)`

- 参数：
  - dir : `String`  
    目标文件夹的路径  
    可以直接创建多层，不需要逐层创建
- 返回值：是否成功创建
- 返回值类型：`Boolean`

<br>

### 删除文件 / 文件夹  

`file.delete(path)`

- 参数：
  - path : `String`  
    目标文件 / 文件夹的路径
- 返回值：是否成功删除
- 返回值类型：`Boolean`

<br>

### 判断文件 / 文件夹是否存在  

`file.exists(path)`

- 参数：
  - path : `String`  
    目标文件 / 文件夹的路径
- 返回值：目标是否存在
- 返回值类型：`Boolean`

<br>

### 复制文件 / 文件夹到指定位置  

`file.copy(from,to)`

- 参数：
  - from : `String`  
    源文件 / 文件夹的路径

  - to : `String`  
    目标文件 / 文件夹的位置
- 返回值：是否复制成功
- 返回值类型：`Boolean`

<br>

### 移动文件 / 文件夹到指定位置  

`file.move(from,to)`

- 参数：
  - from : `String`  
    源文件 / 文件夹的路径

  - to : `String`  
    目标文件 / 文件夹的位置
- 返回值：是否复制成功
- 返回值类型：`Boolean`

<br>

### 重命名指定文件 / 文件夹  

`file.rename(from,to)`

- 参数：
  - from : `String`  
    文件 / 文件夹的旧名字

  - to : `String`  
    新名字
- 返回值：是否复制成功
- 返回值类型：`Boolean`

<br>

------

## 系统调用 API

下面这些API提供了执行一些系统调用的接口

### 调用shell执行指定系统命令

`system.cmd(cmd,callback[,timeLimit])`

- 参数：
  - cmd : `String`  
    执行的系统命令
  - callback : `Function`  
    命令执行的进程结束之后返回数据使用的回调函数
  - timeLimit : `Integer`  
    （可选参数）运行命令进程运行的最长时间，单位为毫秒  
    默认为`-1`，即不限制最长运行时间
- 返回值：是否成功启动命令
- 返回值类型：`Boolean`

注：参数callback的回调函数原型：`function(exitcode,output)`  

- exitcode : `Integer`    
  进程退出码
- output : `Integer`  
  进程标准输出和标准错误输出的内容

注意！这里执行的不是MC命令系统的命令  
此函数不会等待系统执行完后再返回，而是命令执行完后由引擎自动调用给出的回调函数来实现返回结果，即所谓的异步执行

<br>

------

## 网络接口 API

下面这些API为脚本提供了基本的网络接口。  
如果有更复杂的需求，可以使用各自语言平台的网络库来完成任务  

### 发送一个同步HTTP请求  

`network.requestSync(url,method,data)`

- 参数：

  - url : `String`  
    请求的目标地址
  - method : `String`  
    请求发送方式，可选项有 `"GET"` 和 `"POST"`
  - data : `String`  
    发送的数据，形式为键 - 值对

- 返回值类型： `Object<Integer,String>`

  - 对于返回的某个执行结果对象res，有如下这些成员：  

  | 成员       | 含义                          | 类型      |
  | ---------- | ----------------------------- | --------- |
  | res.status | HTTP响应码，如200代表请求成功 | `Integer` |
  | res.data   | HTTP响应返回的具体数据        | `String`  |

<br>

### 发送一个异步HTTP请求  

`network.request(url,method,data,callback)`

- 参数：
  - url : `String`  
    请求的目标地址
  - method : `String`  
    请求发送方式，可选项有 `"GET"` 和 `"POST"`
  - data : `String`  
    发送的数据，形式为键 - 值对
  - callback : `Function`  
    当请求返回时执行的回调函数，用于回传结果。
- 返回值：是否成功发送请求
- 返回值类型：`Boolean`

注：参数callback的回调函数原型：`function(status,result)`  

- status : `Integer`    
  返回的HTTP响应码，如200代表请求成功
- result : `String`  
  返回的具体数据

如果在回调函数中返回`false`，等同于拦截这个命令的执行。

> 异步请求的回调函数可能与其他线程代码同时执行，使用时注意潜在的数据竞争和死锁问题   

<br>

[<< 返回目录](README.md)