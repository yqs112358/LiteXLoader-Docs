# LiteXLoader - 玩家 API

[<< 返回目录](README.md)

> 在LXL中，使用**「玩家对象」**来操作和获取某一个玩家的相关信息。

## 获取一个玩家对象

获取玩家对象有三种方式：

1. 通过注册**事件监听**函数，获取到BDS给出的与相关事件有关的玩家对象  
   详见[事件监听文档 - EventAPI](EventApi.md)

2. 通过**玩家名**或者**xuid**手动生成玩家对象  
   通过此函数来手动生成对象，注意，你要获取的玩家必须是在线状态，否则会获取失败

   `mc.getPlayer(info)`

   - 参数：
     1. info : `String`
     
        玩家的名字或者Xuid  
   - 返回值：玩家对象  
   - 返回值类型：`Player` 
     - 如返回值为 `Null` 则表示获取玩家失败
   
3. 获取**所有在线玩家**的列表  
   此函数会返回一个玩家对象的数组，其中每个对象都对应了一个服务器中的玩家

   `mc.getPlayerList()`

   - 返回值：在线的玩家对象列表
   - 返回值类型：`Array<Player,Player,...>`  



## 玩家对象 - 属性

每一个玩家对象都包含一些固定的对象属性。对于某个特定的玩家对象`pl`，有以下这些属性

- 属性 `pl.name` : `String`
  玩家名
- 属性 `pl.xuid` : `String`
  玩家Xuid
- 属性 `pl.pos` : `FloatPos`
  玩家所在坐标
- 属性 `pl.realName` : `String`
  玩家的真实名字（即使改名后也不变）
- 属性 `pl.ip` : `String`
  玩家设备的IP地址

这些对象属性都是只读的，无法被修改



## 玩家对象 - 函数

每一个玩家对象都包含一些可以执行的成员函数（成员方法）。对于某个特定的玩家对象`pl`，有以下这些函数

### 判断玩家是否为OP  
`pl.isOP()`

- 返回值：玩家是否为OP
- 返回值类型：`Boolean`  



### 断开玩家连接  
`pl.kick([msg])`

- 参数：
    1. msg(可选参数) : `String`
       被踢出玩家出显示的断开原因。如果不传入，默认为“正在从服务器断开连接”  
- 返回值：是否成功断开连接
- 返回值类型：`Boolean`



### 发送一个文本给玩家  
`pl.tell(msg[,type])`
- 参数：
    1. msg : `String`
       待发送的文本  

    2. type(可选参数) : `Number`
       发送的文本消息类型，默认为0

       - 0 Raw 普通消息

       - 1 Chat 聊天消息

       - 5 Tip 物品栏上方的消息

       - 9 Json Json格式消息
- 返回值：是否成功发送
- 返回值类型：`Boolean`



### 传送玩家至指定位置  
`pl.teleport(pos)`

- 参数：
    1. pos : `FloatPos`
       目标位置坐标 
- 返回值：是否成功传送
- 返回值类型：`Boolean`



### 杀死玩家  

`pl.kill()`

- 返回值：是否成功执行
- 返回值类型：`Boolean`



### 重命名玩家  

`pl.rename(newname)`

- 参数：
  1. newname : `String`
     玩家的新名字  
- 返回值：是否重命名成功
- 返回值类型：`Boolean`



### 查询玩家背包  
`pl.getPack()`

- 返回值：
- 返回值类型：



### 获取玩家手持物品  
`pl.getHand()`

- 返回值：玩家当前手持的物品对象
- 返回值类型：`Item`



### 查询玩家操作权限等级  

`pl.getPlayerPermLevel()`

- 返回值：目标玩家的操作权限
  - 0 : Normal
  - 1 : Privileged
  - 2 : AutomationPlayer
  - 3 : OperatorOnly
  - 4 : ConsoleOnly  
- 返回值类型：`Number`



### 修改玩家操作权限等级  

`pl.setPlayerPermLevel(level)`

- 参数：

  1. level : `Number`
     目标操作权限等级

     - 0 : Normal

     - 1 : Privileged

     - 2 : AutomationPlayer

     - 3 : OperatorOnly

     - 4 : ConsoleOnly  
- 返回值：是否成功修改
- 返回值类型：`Boolean`



### 获取玩家计分板值  
`pl.getScoreBoard(name)`

- 参数：
    1. name : `String`
       计分板名称  
- 返回值：计分板上的数值
- 返回值类型：`Number`



### 设置玩家计分板值  
`pl.setScoreBoard(name,value)`

- 参数：
    1. name : `String`
       计分板名称  

    2. value : `Number`
       设置的数值  
- 返回值：是否设置成功
- 返回值类型：`Boolean`



### 设置玩家自定义侧边栏计分板  

`pl.setScoreBoard(title,data)`

- 参数：
  1. title : `String`
     侧边栏标题  

  2. data : `Array<String,String,...>`
     列表字符串数组  
- 返回值：是否成功设置
- 返回值类型：`Boolean`



### 移除玩家自定义侧边栏计分板  

`pl.removeScoreBoard()`

- 返回值：是否成功移除
- 返回值类型：`Boolean`



### 设置玩家看到的自定义Boss血条  

`pl.setBossBar(title,percent)`

- 参数：
  1. title : `String`
     自定义血条标题  
  2. percent : `Number`
     血条中的血量百分比，有效范围为0~100。0为空血条，100为满
- 返回值：是否成功设置
- 返回值类型：`Boolean`



### 移除玩家的自定义Boss血条  

`pl.removeBossBar()`

- 返回值：是否成功移除
- 返回值类型：`Boolean`



### 提高玩家经验等级 
`pl.addLevel(count)`
- 参数：
    1. count : `Number`
       要提升的经验等级（整数）  
- 返回值：是否设置成功
- 返回值类型：`Boolean`



### 传送玩家至指定服务器  

`pl.transServer(server,port)`

- 参数：
  1. server : `String`
     目标服务器IP / 域名

  2. port : `Number`
     目标服务器端口  
- 返回值：是否成功传送
- 返回值类型：`Boolean` 