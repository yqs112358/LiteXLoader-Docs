# LiteXLoader - 通用 API
[<< 返回目录](README.md)

所有注入到引擎中的API被划分为各种不同的功能模块，而下列这些内容则是在编写大部分功能时都会涉及到的内容。  

## API文档描述约定

> 首先，为了文档的格式统一和规范，规定一下LXL统一的文档描述约定

对于接下来你看到的所有API文档，都有这样的写作规则：

1. 函数参数按照 **参数名 : 参数类型** 格式描述  
   例如： cmd : `String` 表示一个**字符串**类型的变量cmd  
   如果参数类型出现`Array<...>`表示一个以<>内的变量为内容的数组 / 列表  
   
   
   
2. 如果在参数描述处出现 `可选参数` 则代表你可以不传入这个参数。  
   当你不传入这个参数的时候，引擎将使用描述中给出的默认值。

   

3. 如果在API函数原型后出现 `xx环境下别名：...` 则表示在某种特定语言下当前API可以有**另一种**名字或者用法。此时默认的函数名和特定的别名都可以使用，达到的效果**相同**。  
   举例：通用API中提到的`log`和`setFutureTask`函数即是实例。

<br>

## 数据类型
> 接下来，你需要熟悉几种在使用 API 过程中会频繁用到的数据类型

### 通用数据类型约定
虽然脚本语言通常是弱类型的，不需要关注具体的数据类型，但由于LiteXLoader支持多种不同的脚本语言，为了方便对接API，下面定义一些通用的数据类型。请你首先务必熟悉这些称呼的意思。  
- `Null` - 空（未定义，不存在,无返回值等等）
- `Number` - 整数 / 实数（小数，浮点数）
- `String` - 字符串
- `ByteBuffer` - 字符数组（字节串，字符缓冲区）
- `Boolean` - 布尔型
- `Function` - 函数（方法）
- `Array` - 数组（列表）
- `Object` - 对象（映射，字典，表）
- `Player` - 玩家对象（详见PlayerAPI）
- `Entity` - 实体对象（详见EntityAPI）
- `Block` - 方块对象（详见BlockAPI）
- `Item` - 物品栏物品对象（详见ItemAPI）
- `Form` - 表单对象（详见GUIAPI）
- `IntPos` - 整数位置 坐标对象（详解在下）
- `FloatPos` - 实数位置 坐标对象（详解在下）

<br>

### 游戏元素对象
对于游戏元素的索引，在脚本中使用一个专门类型的变量来跟踪每一个游戏元素，并称其为「xx对象」，如「玩家对象」或者「方块对象」。你可以将其理解为元素的唯一标识符。   

<br>

### 位置坐标对象
在游戏中，数量众多的 API 都需要提供位置坐标。引擎采用 `IntPos` 和 `FloatPos` 类型的对象来标示坐标，称之为「位置坐标对象」。  
1. `IntPos`对象
   它的成员均为**整数**，多用来表示**方块坐标**等用整数表示的位置  
   对于一个 `IntPos` 类型变量 pos，有如下这些属性：  

   | 成员    | 含义                           | 类型           |
   | ------- | ------------------------------ | -------------- |
   | pos.x   | x坐标                          | `Number`，整数 |
   | pos.y   | y坐标                          | `Number`，整数 |
   | pos.z   | z坐标                          | `Number`，整数 |
   | pos.dim | 维度，0 主世界，1 下界，2 末地 | `Number`，整数 |

    > 如果某种情况下维度无效，或者无法获取，你会发现`dim`的值为-1。

   

2. `FloatPos`对象
   它的x,y,z成员均为**实数**，多用来表示**实体坐标**等用实数表示的位置  
   对于一个 `FloatPos` 类型变量 pos：  

    - 成员 `pos.x` : `Number`

       x坐标（实数）  

    - 成员 `pos.y` : `Number`
   
    y坐标（实数）  
   
    - 成员 `pos.z` : `Number`
   
    z坐标（实数）  
   
    - 成员 `pos.dim` : `Number`
   
    维度（整数）：0 主世界，1 下界，2 末地
   
    > 如果某种情况下维度无效，或者无法获取，你会发现`dim`的值为-1。


<br>

---

## 通用 API
这些是在编写脚本过程中到处需要使用到的 API  

> 注：这些通用接口都被封装进 mc 对象中

### 执行一条后台命令  

`mc.runcmd(cmd)`

- 参数：
  - cmd : `String`  
    待执行的命令  
- 返回值：是否执行成功
- 返回值类型： `Boolean`

<br>

### 执行一条后台命令（强化版）  

`mc.runcmdEx(cmd)`

- 参数：
  - cmd : `String`  
    待执行的命令  
- 返回值：结果`Object` 
  - 成员 result : `Boolean`  
    表示是否执行成功  
    
  - 成员 output : `String`  
    返回BDS执行命令后的输出结果  
- 返回值类型： `Object<Boolean,String>`

<br>

### 以指定玩家身份执行一条命令 

`mc.runCmdAs(player,cmd)`

- 参数：
  - player : `Player`  
    目标玩家对象  

  - cmd : `String`  
    待执行的命令  
- 返回值：是否执行成功
- 返回值类型： `Boolean`   

<br>

### 注册一个命令  

`mc.registerCmd(cmd,description[,level])`

- 参数：
  - cmd : `String`  
    待注册的命令

  - description : `String`  
    命令描述文本  

  - level(可选参数) : `Number`  
    命令的注册等级，默认为4  
    0 : Normal  
    1 : Privileged  
    2 : AutomationPlayer  
    3 : OperatorOnly  
    4 : ConsoleOnly
- 返回值：是否成功注册
- 返回值类型：`Boolean`

<br>

### 设置服务器Motd字符串  
`mc.setServerMotd(motd)`

- 参数：
    - motd : `String`  
      目标Motd字符串  
- 返回值：是否设置成功
- 返回值类型：`Boolean`

<br>

---
## 辅助 API
这些是在编写脚本过程中到处需要使用到的，起辅助作用的 API  

### 输出到控制台  
`log(data1,data2,...)` (Lua环境下别名：`print`)

- 参数：
    - dataN : `任意类型`  
      待输出的变量或者数据  
      可以是任意类型，参数数量可以是任意个
- 返回值：无

<br>

### 获取当前时间字符串  

> 注：这个接口被封装进 system 对象中

`system.getTimeStr()`

- 返回值：当前的时间字符串，使用当地时区和24小时制。  

  形如`2021-04-03 19:15:01`

- 返回值类型：`String`

<br>

### 获取当前的时间对象

> 注：这个接口被封装进 system 对象中

`system.getTimeObj()`

- 返回值：一个时间对象（`Object`）
    - 成员 Y : `Number`  
      年份数值（4位）  
      
    - 成员 M : `Number`  
      月份数值
      
    - 成员 D : `Number`  
      天数数值
      
    - 成员 h : `Number`  
      小时数值（24小时制）
      
    - 成员 m : `Number`  
      分钟数值
      
    - 成员 s : `Number`  
      秒数值
      
    - 成员 ms : `Number`  
    毫秒数值
- 返回值类型： `Object<Number,Number,Number,Number,Number,Number,Number>`

<br>

### 推迟一段时间执行函数  
`setFutureTask(func,msec)` (Js环境下别名：`setTimeout`)

- 参数：

    - func : `Function`  
      待执行的函数

    - msec : `Number`  
      推迟执行的时间（毫秒）
- 返回值：此任务ID
- 返回值类型：`Number`
> 推迟执行的函数可能与其他线程代码同时执行，使用时注意潜在的数据竞争和死锁问题  

<br>

### 推迟一段时间执行代码段（eval）  
`setFutureTask(code,msec)` (Js环境下别名：`setTimeout`)

- 参数：

    - code : `String`  
      待执行的代码段

    - msec : `Number`  
      推迟执行的时间（毫秒）
- 返回值：此任务ID
- 返回值类型：`Number`
> 推迟执行的代码可能与其他线程代码同时执行，使用时注意潜在的数据竞争和死锁问题  

<br>

### 设置周期执行函数  
`setLoopTask(func,msec)` (Js环境下别名：`setInterval`)

- 参数：
    - func : `Function`  
      待执行的函数

    - msec : `Number`  
      执行间隔周期（毫秒）
- 返回值：此任务ID
- 返回值类型： `Number`
> 周期执行的函数可能与其他线程代码同时执行，使用时注意潜在的数据竞争和死锁问题  

<br>

### 设置周期执行代码段（eval）  
`setLoopTask(code,msec)` (Js环境下别名：`setInterval`)

- 参数：
    - code : `String`  
      待执行的代码段

    - msec : `Number`  
      执行间隔周期（毫秒）
- 返回值：此任务ID
- 返回值类型： `Number`
> 周期执行的代码可能与其他线程代码同时执行，使用时注意潜在的数据竞争和死锁问题   

<br>

### 取消延时 / 周期执行项  
`cancelTask(taskid)` (Js环境下别名：`clearInterval`)

- 参数：
    - timerid : `Number`  
      由前几个函数返回的任务ID
- 返回值：是否取消成功
- 返回值类型： `Boolean`

<br>

### 随机生成一个GUID  
`randomGuid()` 

- 返回值：一个随机生成的唯一标识符GUID
- 返回值类型： `String`

<br>

### 启动一个新的脚本插件
(仅用于运行时动态加载插件，若要导入外部代码请用各自语言的import或者require)
`loadPlugin(path)`

- 参数：
    - path : `String`  
      要加载的插件文件路径（如`addplugin.js`)

    > 只能加载与当前开发语言相同的插件，比如说在js插件中不能动态加载.lua文件

- 返回值：是否启动成功

- 返回值类型： `Boolean`

<br>

### 获取LiteXLoader加载器版本
`getLxlVersion()`

- 返回值：加载器版本号，格式`主版本.次版本.开发版本`。如`1.0.1`
- 返回值类型： `String`

<br>