# LiteXLoader - 通用 API
[<< 返回目录](README.md)

所有注入到引擎中的API被划分为各种不同的功能模块，而下列这些内容则是在编写大部分功能时都会涉及到的内容。

## 通用 API
下面这些，是在编写脚本过程中到处需要使用到的 API  。  
可以看到，这些通用接口都被封装进了 mc 对象中。

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
  
- 返回值：命令执行结果`Object` 

- 返回值类型： `Object<Boolean,String>`

  - 对于返回的某个执行结果对象res，有如下这些成员：  

  | 成员       | 含义                    | 类型      |
  | ---------- | ----------------------- | --------- |
  | res.result | 是否执行成功            | `Boolean` |
  | res.output | BDS执行命令后的输出结果 | `String`  |


> 注：runcmdEx 与普通 runcmd 实现区别非常大，在于 Ex 版本拥有**隐藏执行**的机制，执行结果不会输出至控制台，因此如果有需要，要手动用 log 函数将结果输出

<br>

### 注册一个命令  

`mc.registerCmd(cmd,description[,level])`

- 参数：
  - cmd : `String`  
    待注册的命令
  - description : `String`  
    命令描述文本  
  - level : `Integer`  
    （可选参数）命令的注册等级，默认为 0   

  | 命令注册等级 | 执行权限情况           |
  | ------------ | ---------------------- |
  | 0            | 所有人都可以执行       |
  | 1            | 只有OP可以执行         |
  | 4            | 只有后台控制台可以执行 |
  
- 返回值：是否成功注册

- 返回值类型：`Boolean`

> 也就是说，注册玩家命令和注册后台控制台命令用这一个 registerCmd 即可全部实现。  
> 注册玩家命令使用等级0和1，注册控制台命令使用等级4

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
    - 待输出的变量或者数据  
      可以是任意类型，参数数量可以是任意个
- 返回值：无

<br>

### 获取当前时间字符串  

（注：这个接口被封装进了 system 对象中）

`system.getTimeStr()`

- 返回值：当前的时间字符串，使用当地时区和24小时制。  
  形如`2021-04-03 19:15:01`
- 返回值类型：`String`

<br>

### 获取当前的时间对象

（注：这个接口被封装进了 system 对象中）

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

### 推迟一段时间执行函数  
`setTimeout(func,msec)`

- 参数：

    - func : `Function`  
      待执行的函数

    - msec : `Integer`  
      推迟执行的时间（毫秒）
- 返回值：此任务ID
- 返回值类型：`Integer`
> 推迟执行的函数可能与其他线程代码同时执行，使用时注意潜在的数据竞争和死锁问题  

<br>

### 推迟一段时间执行代码段（eval）  
`setTimeout(code,msec)`

- 参数：

    - code : `String`  
      待执行的代码段

    - msec : `Integer`  
      推迟执行的时间（毫秒）
- 返回值：此任务ID
- 返回值类型：`Integer`
> 推迟执行的代码可能与其他线程代码同时执行，使用时注意潜在的数据竞争和死锁问题  

<br>

### 设置周期执行函数  
`setInterval(func,msec)`

- 参数：
    - func : `Function`  
      待执行的函数

    - msec : `Integer`  
      执行间隔周期（毫秒）
- 返回值：此任务ID
- 返回值类型： `Integer`
> 周期执行的函数可能与其他线程代码同时执行，使用时注意潜在的数据竞争和死锁问题  

<br>

### 设置周期执行代码段（eval）  
`setInterval(code,msec)`

- 参数：
    - code : `String`  
      待执行的代码段

    - msec : `Integer`  
      执行间隔周期（毫秒）
- 返回值：此任务ID
- 返回值类型： `Integer`
> 周期执行的代码可能与其他线程代码同时执行，使用时注意潜在的数据竞争和死锁问题   

<br>

### 取消延时 / 周期执行项  
`clearInterval(taskid)`

- 参数：
    - timerid : `Integer`  
      由前几个函数返回的任务ID
- 返回值：是否取消成功
- 返回值类型： `Boolean`

<br>

### 启动一个新的脚本插件
(仅用于运行时动态加载插件，若要导入外部代码请用各自语言的import或者require)
`loadPlugin(path)`

- 参数：
    - path : `String`  
      要加载的插件文件路径（如`addplugin.js`)

- 返回值：是否启动成功
- 返回值类型： `Boolean`

> 只能加载与当前开发语言相同的插件，比如说在js插件中不能动态加载.lua文件

<br>

### 获取LiteXLoader加载器版本
`getLxlVersion()`

- 返回值：加载器版本号，格式`主版本.次版本.开发版本`。如`1.0.1`
- 返回值类型： `String`

<br>

[<< 返回目录](README.md)