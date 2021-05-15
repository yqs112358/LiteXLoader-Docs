# LiteXLoader - 事件 API
> 这些是在监听**游戏事件**并做出响应时需要用到的函数

## 监听 API
注册指定的监听函数。当事件发生时，监听函数将被引擎调用以供处理相关事件。  

### 新增监听器  
`mc.listen(event,callback)`

- 参数：
    1. event : `String`
        要监听的事件名（见下方监听事件列表）
    2. callback : `Function`
        注册的监听函数（函数相关参数见下）  
      当指定的事件发生时，BDS会调用你给出的监听函数，并传入相应的参数
- 返回值：是否成功监听事件
- 返回值类型：`Boolean` 



---
## 监听事件列表
目前，LiteXLoader支持如下这些事件的监听。

### `"OnJoin"` - 玩家进入服务器
- 监听函数原型
`function(player)`
- 参数：
    1. player : `Player`
    进入服务器的玩家对象
- 拦截事件：不可以拦截



### `"OnLeft"` - 玩家离开服务器
- 监听函数原型
`function(player)`
- 参数：
    1. player : `Player`
    离开服务器的玩家对象
- 拦截事件：不可以拦截



### `"OnRespawn"` - 玩家重生
- 监听函数原型
`function(player)`
- 参数：
    1. player : `Player`
    重生的玩家对象
- 拦截事件：不可以拦截



### `"OnChangeDim"` - 玩家切换维度
- 监听函数原型
`function(player)`
- 参数：
    1. player : `Player`
    切换维度的玩家对象
- 拦截事件：不可以拦截



### `"OnPlayerCmd"` - 玩家执行命令
- 监听函数原型
`function(player,cmd)`
- 参数：
    1. player : `Player`
    执行命令的玩家对象
    2. cmd : `String`
    执行的命令
- 拦截事件：函数返回`false`



### `"OnChat"` - 玩家发送聊天信息
- 监听函数原型
`function(player,msg)`
- 参数：
    1. player : `Player`
    发送聊天信息的玩家对象
    2. msg : `String`
    发送的聊天消息
- 拦截事件：函数返回`false`



### `"OnAttack"` - 玩家攻击实体
- 监听函数原型
`function(player,entiey)`
- 参数：
    1. player : `Player`
    攻击实体的玩家对象
    2. entity : `Entity`
    被攻击的实体对象
- 拦截事件：函数返回`false`



### `"OnUseItem"` - 玩家使用物品
- 监听函数原型
`function(player,item)`
- 参数：
    1. player : `Player`
    使用物品的玩家对象
    2. item : `Item`
    被使用的物品对象
- 拦截事件：函数返回`false`



### `"OnTakeItem"` - 玩家捡起物品
- 监听函数原型
`function(player,item)`
- 参数：
    1. player : `Player`
    捡起物品的玩家对象
    2. item : `Item`
    被捡起的物品对象
- 拦截事件：函数返回`false`



### `"OnDropItem"` - 玩家丢出物品
- 监听函数原型
`function(player,item)`
- 参数：
    1. player : `Player`
    丢出物品的玩家对象
    2. item : `Item`
    被丢出的物品对象
- 拦截事件：函数返回`false`



### `"OnDestroyBlock"` - 玩家破坏方块
- 监听函数原型
`function(player,block,pos)`
- 参数：
    1. player : `Player`
    破坏方块的玩家对象
    2. block : `Block`
    被破坏的方块对象
    3. pos : `IntPos`
    被破坏的方块坐标
- 拦截事件：函数返回`false`



### `"OnPlaceBlock"` - 玩家放置方块
- 监听函数原型
`function(player,block)`
- 参数：
    1. player : `Player`
    放置方块的玩家对象
    2. block : `Block`
    被放置的方块对象
    3. pos : `IntPos`
    被放置的方块坐标
- 拦截事件：函数返回`false`



### `"OnOpenChest"` - 玩家打开箱子
- 监听函数原型
`function(player,pos)`
- 参数：
    1. player : `Player`
    打开箱子的玩家对象
    2. pos : `IntPos`
    被打开的箱子坐标
- 拦截事件：函数返回`false`



### `"OnCloseChest"` - 玩家关闭箱子
- 监听函数原型
`function(player,pos)`
- 参数：
    1. player : `Player`
    关闭箱子的玩家对象
    2. pos : `IntPos`
    被关闭的箱子坐标
- 拦截事件：函数返回`false`



### `"OnOpenBarrel"` - 玩家打开木桶
- 监听函数原型
`function(player,pos)`
- 参数：
    1. player : `Player`
    打开木桶的玩家对象
    2. pos : `IntPos`
    被打开的木桶坐标
- 拦截事件：函数返回`false`



### `"OnCloseBarrel"` - 玩家关闭木桶
- 监听函数原型
`function(player)`
- 参数：
    1. player : `Player`
    关闭木桶的玩家对象
    2. pos : `IntPos`
    被关闭的木桶坐标
- 拦截事件：函数返回`false`



### `"OnChangeSlot"` - 玩家向容器放入 / 取出物品
- 监听函数原型
`function(player,container,slotNum,isPutIn,item)`
- 参数：
    1. player : `Player`
    操作容器的玩家对象
    2. container : `Block`
    被操作的容器的方块对象
    3. slotNum : `Number`
    操作容器的格子位置（第x个格子）
    4. isPutIn : `Boolean`
       是否为放入物品
        - 为 `true` 表示正在放入物品
        - 为 `false` 表示正在取出物品
    5. item : `Item`
    被操作的物品对象
- 拦截事件：不可以拦截



### `"OnMobDie"` - 生物死亡（包括玩家）
- 监听函数原型
`function(mob,source)`
- 参数：
    1. mob : `Entity`
    死亡的实体指针
    2. source : `Entity`
    伤害来源的实体指针
- 拦截事件：函数返回`false`



### `"OnMobHurt"` - 生物受伤（包括玩家）
- 监听函数原型
`function(mob,source)`
- 参数：
    1. mob : `Entity`
    受伤的实体指针
    2. source : `Entity`
    伤害来源的实体指针
- 拦截事件：函数返回`false`



### `"OnExplode"` - 发生爆炸
- 监听函数原型
`function(source,pos)`
- 参数：
    1. source : `Entity`
    爆炸来源的实体指针
    2. pos : `FloatPos`
    爆炸发生的坐标
- 拦截事件：函数返回`false`



### `"OnCmdBlockExecute"` - 命令方块执行命令
- 监听函数原型
`function(cmd,pos)`
- 参数：
    1. cmd : `String`
    执行的命令
    2. pos : `IntPos`
    执行命令的命令方块坐标
- 拦截事件：函数返回`false`



### `"OnServerStarted"` - 服务器启动完毕
- 监听函数原型
`function()`
- 参数：
    - 无
- 拦截事件：不可以拦截



### `"OnServerCmd"` - 服务端执行后台命令
- 监听函数原型
`function(cmd)`
- 参数：
    1. cmd : `String`
    执行的后台命令
- 拦截事件：函数返回`false`