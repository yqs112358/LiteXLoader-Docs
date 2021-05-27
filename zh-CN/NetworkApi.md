# LiteXLoader - 网络 API

[<< 返回目录](README.md)

这里为脚本提供了基本的网络能力支持。  
如果有更复杂的需求，可以使用各自语言平台的网络库来完成任务  

<br>

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
    当请求返回时执行的回调函数，用于回传参数。  
    回调函数原型：`function(status,result)`  
    其中，status 类型为`Integer`，代表HTTP响应码，如200代表请求成功  
    result类型为`String`，为返回的具体数据
- 返回值：是否成功发送请求
- 返回值类型：`Boolean`

> 异步请求的回调函数可能与其他线程代码同时执行，使用时注意潜在的数据竞争和死锁问题   

<br>

[<< 返回目录](README.md)