# LiteXLoader - 事件 API
> 除了 **通用 API** 之外，还有这些在监听事件时需要额外使用到的功能  

## 监听 API
注册指定的监听函数。当事件发生时，监听函数将被引擎调用以供处理相关事件。  
### 新增监听器  
`listen(event,callback)`
- 参数：
    1. event : `String`  
    要监听的事件名（见下方监听事件列表）
    2. callback : `Function`  
    注册的监听函数（函数相关参数见下） 
- 返回值：是否成功监听事件
- 返回值类型：`Boolean`   
<br>

---
## 监听事件列表
目前，LiteXLoader支持如下这些事件的监听。

### `"OnJoin"` - 玩家进入服务器
- 监听函数原型  
`function(player)`
- 参数：
    1. player : `Pointer`  
    进入服务器的玩家指针
- 拦截事件：不可以拦截
<br>

### `"OnLeft"` - 玩家离开服务器
- 监听函数原型  
`function(player)`
- 参数：
    1. player : `Pointer`  
    离开服务器的玩家指针
- 拦截事件：不可以拦截
<br>

### `"OnRespawn"` - 玩家重生
- 监听函数原型  
`function(player)`
- 参数：
    1. player : `Pointer`  
    重生的玩家指针
- 拦截事件：不可以拦截
<br>

### `"OnChangeDim"` - 玩家切换维度
- 监听函数原型  
`function(player)`
- 参数：
    1. player : `Pointer`  
    切换维度的玩家指针
- 拦截事件：不可以拦截
<br>

### `"OnPlayerCmd"` - 玩家执行命令
- 监听函数原型  
`function(player,cmd)`
- 参数：
    1. player : `Pointer`  
    执行命令的玩家指针
    2. cmd : `String`  
    执行的命令
- 拦截事件：函数返回`false`
<br>

### `"OnChat"` - 玩家发送聊天信息
- 监听函数原型  
`function(player,msg)`
- 参数：
    1. player : `Pointer`  
    发送聊天信息的玩家指针
    2. msg : `String`  
    发送的聊天消息
- 拦截事件：函数返回`false`
<br>

### `"OnAttack"` - 玩家攻击实体
- 监听函数原型  
`function(player,entiey)`
- 参数：
    1. player : `Pointer`  
    攻击实体的玩家指针
    2. entity : `Pointer`  
    被攻击的实体指针
- 拦截事件：函数返回`false`
<br>

### `"OnUseItem"` - 玩家使用物品
- 监听函数原型  
`function(player,item)`
- 参数：
    1. player : `Pointer`  
    使用物品的玩家指针
    2. item : `Pointer`  
    被使用的物品指针
- 拦截事件：函数返回`false`
<br>

### `"OnTakeItem"` - 玩家捡起物品
- 监听函数原型  
`function(player,item)`
- 参数：
    1. player : `Pointer`  
    捡起物品的玩家指针
    2. item : `Pointer`  
    被捡起的物品指针
- 拦截事件：函数返回`false`
<br>

### `"OnDropItem"` - 玩家丢出物品
- 监听函数原型  
`function(player,item)`
- 参数：
    1. player : `Pointer`  
    丢出物品的玩家指针
    2. item : `Pointer`  
    被丢出的物品指针
- 拦截事件：函数返回`false`
<br>

### `"OnDestroyBlock"` - 玩家破坏方块
- 监听函数原型  
`function(player,block,pos)`
- 参数：
    1. player : `Pointer`  
    破坏方块的玩家指针
    2. block : `Pointer`  
    被破坏的方块指针
    3. pos : `IntPos`  
    被破坏的方块坐标
- 拦截事件：函数返回`false`
<br>

### `"OnPlaceBlock"` - 玩家放置方块
- 监听函数原型  
`function(player,block)`
- 参数：
    1. player : `Pointer`  
    放置方块的玩家指针
    2. block : `Pointer`  
    被放置的方块指针
    3. pos : `IntPos`  
    被放置的方块坐标
- 拦截事件：函数返回`false`
<br>

### `"OnOpenChest"` - 玩家打开箱子
- 监听函数原型  
`function(player,pos)`
- 参数：
    1. player : `Pointer`  
    打开箱子的玩家指针
    2. pos : `IntPos`  
    被打开的箱子坐标
- 拦截事件：函数返回`false`
<br>

### `"OnCloseChest"` - 玩家关闭箱子
- 监听函数原型  
`function(player,pos)`
- 参数：
    1. player : `Pointer`  
    关闭箱子的玩家指针
    2. pos : `IntPos`  
    被关闭的箱子坐标
- 拦截事件：函数返回`false`
<br>

### `"OnOpenBarrel"` - 玩家打开木桶
- 监听函数原型  
`function(player,pos)`
- 参数：
    1. player : `Pointer`  
    打开木桶的玩家指针
    2. pos : `IntPos`  
    被打开的木桶坐标
- 拦截事件：函数返回`false`
<br>

### `"OnCloseBarrel"` - 玩家关闭木桶
- 监听函数原型  
`function(player)`
- 参数：
    1. player : `Pointer`  
    关闭木桶的玩家指针
    2. pos : `IntPos`  
    被关闭的木桶坐标
- 拦截事件：函数返回`false`
<br>

### `"OnChangeSlot"` - 玩家向容器放入 / 取出物品
- 监听函数原型  
`function(player,container,slotNum,isPutIn,item)`
- 参数：
    1. player : `Pointer`  
    操作容器的玩家指针
    2. container : `Pointer`  
    被操作的容器的方块指针
    3. slotNum : `Number`  
    操作容器的格子位置（第x个格子）
    4. isPutIn : `Boolean`  
    是否为放入物品
        - 为 `true` 表示正在放入物品
        - 为 `false` 表示正在取出物品
    5. item : `Pointer`  
    被操作的物品指针
- 拦截事件：不可以拦截
<br>

### `"OnMobDie"` - 生物死亡（包括玩家）
- 监听函数原型  
`function(mob,source)`
- 参数：
    1. mob : `Pointer`  
    死亡的实体指针
    2. source : `Pointer`  
    伤害来源的实体指针
- 拦截事件：函数返回`false`
<br>

### `"OnMobHurt"` - 生物受伤（包括玩家）
- 监听函数原型  
`function(mob,source)`
- 参数：
    1. mob : `Pointer`  
    死亡的实体指针
    2. source : `Pointer`  
    伤害来源的实体指针
- 拦截事件：函数返回`false`
<br>

### `"OnExplode"` - 发生爆炸
- 监听函数原型  
`function(source,pos)`
- 参数：
    1. source : `Pointer`  
    爆炸来源的实体指针
    2. pos : `FloatPos`  
    爆炸发生的坐标
- 拦截事件：函数返回`false`
<br>

### `"OnCmdBlockExecute"` - 命令方块执行命令
- 监听函数原型  
`function(cmd,pos)`
- 参数：
    1. cmd : `String`  
    执行的命令
    2. pos : `IntPos`  
    执行命令的命令方块坐标
- 拦截事件：函数返回`false`
<br>

### `"OnServerStarted"` - 服务器启动完毕
- 监听函数原型  
`function()`
- 参数：
    - 无
- 拦截事件：不可以拦截
<br>

### `"OnServerCmd"` - 服务端执行后台命令
- 监听函数原型  
`function(cmd)`
- 参数：
    1. cmd : `String`  
    执行的后台命令
- 拦截事件：函数返回`false`
<br>