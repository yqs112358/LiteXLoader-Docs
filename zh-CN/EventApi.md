# LiteXLoader - 事件监听文档

[<< 返回目录](README.md)


事件系统和事件相关的处理代码，将是你编写插件的重要组成部分。  
下面这些API，提供了监听**游戏事件**并做出响应的相关能力。

<br>

## 监听 API

注册指定的监听函数。  
当游戏中的某种事件发生时，你设置的对应的监听函数将被引擎调用，这时候你可以对相关事件进行处理。  

### 新增监听器  
`mc.listen(event,callback)`

- 参数：

    - event : `String`  
      要监听的事件名（见下方监听事件列表）

    - callback : `Function`  
      注册的监听函数（函数相关参数见下）  
      当指定的事件发生时，BDS会调用你给出的监听函数，并传入相应的参数
- 返回值：是否成功监听事件
- 返回值类型：`Boolean` 

<br>

### 拦截事件

在下面的列表中，你会看到一些对 拦截事件 的解释。拦截事件意味着在脚本拦截之后BDS将不再处理这个事件，就像他从没发生过一样。  
举例：拦截某条聊天事件会造成所有人都看不到这条聊天消息  
不过，拦截事件仅对BDS有效。  
也就是说，拦截事件并不影响其他有对应监听的LXL脚本处理这个事件，只是BDS无法再接收到它。

<br>

---
## 监听事件列表
目前，LiteXLoader支持如下这些事件的监听。

### 玩家相关事件

#### `"onJoin"` - 玩家进入服务器
- 监听函数原型
`function(player)`
- 参数：
    - player : `Player`  
      进入服务器的玩家对象

- 拦截事件：不可以拦截

<br>

#### `"onLeft"` - 玩家离开服务器
- 监听函数原型
`function(player)`
- 参数：
    - player : `Player`  
      离开服务器的玩家对象

- 拦截事件：不可以拦截

<br>

#### `"onRespawn"` - 玩家重生
- 监听函数原型
`function(player)`
- 参数：
    - player : `Player`  
      重生的玩家对象

- 拦截事件：不可以拦截

<br>

#### `"onChangeDim"` - 玩家切换维度
- 监听函数原型
`function(player)`
- 参数：
    - player : `Player`  
      切换维度的玩家对象

- 拦截事件：不可以拦截

<br>

#### `"onPlayerCmd"` - 玩家执行命令
- 监听函数原型
`function(player,cmd)`
- 参数：
    - player : `Player`  
      执行命令的玩家对象

    - cmd : `String`  
      执行的命令

- 拦截事件：函数返回`false`

<br>

#### `"onChat"` - 玩家发送聊天信息
- 监听函数原型
`function(player,msg)`
- 参数：
    - player : `Player`  
      发送聊天信息的玩家对象

    - msg : `String`  
      发送的聊天消息

- 拦截事件：函数返回`false`

<br>

#### `"onAttack"` - 玩家攻击实体
- 监听函数原型
`function(player,entiey)`
- 参数：
    - player : `Player`  
      攻击实体的玩家对象

    - entity : `Entity`  
      被攻击的实体对象

- 拦截事件：函数返回`false`

<br>

#### `"onUseItem"` - 玩家使用物品
- 监听函数原型
  `function(player,item)`
- 参数：
    - player : `Player`  
      使用物品的玩家对象

    - item : `Item`  
      被使用的物品对象
- 拦截事件：函数返回`false`

注：Win10客户端玩家单次右键，会在服务端多次激发这个事件，请开发者注意这种情况

<br>

#### `"onTakeItem"` - 玩家捡起物品
- 监听函数原型
`function(player,item)`
- 参数：

    - player : `Player`  
      捡起物品的玩家对象

    - item : `Item`  
      被捡起的物品对象

- 拦截事件：函数返回`false`

<br>

#### `"onDropItem"` - 玩家丢出物品
- 监听函数原型
`function(player,item)`
- 参数：
    - player : `Player`  
      丢出物品的玩家对象

    - item : `Item`  
      被丢出的物品对象

- 拦截事件：函数返回`false`

<br>

#### `"onEat"` - 玩家食用食物

- 监听函数原型
  `function(player,item)`
- 参数：
  - player : `Player`  
    正在吃的玩家对象
  - item : `Item`  
    被吃的物品对象

- 拦截事件：不可以拦截

<br>

#### `"onDestroyBlock"` - 玩家破坏方块
- 监听函数原型
`function(player,block,pos)`
- 参数：
    - player : `Player`  
      破坏方块的玩家对象

    - block : `Block`  
      被破坏的方块对象

    - pos : `IntPos`  
      被破坏的方块坐标

- 拦截事件：函数返回`false`

<br>

#### `"onPlaceBlock"` - 玩家放置方块
- 监听函数原型
`function(player,block)`
- 参数：
    - player : `Player`  
      放置方块的玩家对象

    - block : `Block`  
      被放置的方块对象

    - pos : `IntPos`  
      被放置的方块坐标

- 拦截事件：函数返回`false`

<br>

#### `"onOpenChest"` - 玩家打开箱子
- 监听函数原型
`function(player,pos)`
- 参数：
    - player : `Player`  
      打开箱子的玩家对象

    - pos : `IntPos`  
      被打开的箱子坐标

- 拦截事件：函数返回`false`

<br>

#### `"onCloseChest"` - 玩家关闭箱子
- 监听函数原型
`function(player,pos)`
- 参数：
    - player : `Player`  
      关闭箱子的玩家对象

    - pos : `IntPos`  
      被关闭的箱子坐标

- 拦截事件：函数返回`false`

<br>

#### `"onOpenBarrel"` - 玩家打开木桶
- 监听函数原型
`function(player,pos)`
- 参数：
    - player : `Player`  
      打开木桶的玩家对象

    - pos : `IntPos`  
      被打开的木桶坐标

- 拦截事件：函数返回`false`

<br>

#### `"onCloseBarrel"` - 玩家关闭木桶
- 监听函数原型
`function(player)`
- 参数：
    - player : `Player`  
      关闭木桶的玩家对象

    - pos : `IntPos`  
      被关闭的木桶坐标

- 拦截事件：函数返回`false`

<br>

#### `"onChangeSlot"` - 玩家向容器放入 / 取出物品
- 监听函数原型
  `function(player,container,slotNum,isPutIn,item)`

- 参数：
    - player : `Player`  
      操作容器的玩家对象

    - container : `Block`  
      被操作的容器的方块对象

    - slotNum : `Integer`  
      操作容器的格子位置（第slotNum个格子）

    - isPutIn : `Boolean`  
      是否为放入物品
      - 为 `true` 表示正在放入物品
      - 为 `false` 表示正在取出物品

    - item : `Item`  
      被操作的物品对象

- 拦截事件：不可以拦截

<br>

#### `"onMove"` - 玩家移动

- 监听函数原型
  `function(player,pos)`
- 参数：
  - player : `Player`  
    正在移动的玩家对象
  - pos : `FloatPos`  
    这个玩家当前的位置

- 拦截事件：不可以拦截

<br>

#### `"onSetArmor"` - 玩家改变盔甲栏

- 监听函数原型
  `function(player,slotNum,item)`
- 参数：
  - player : `Player`  
    改变盔甲栏的玩家对象
  - slotNum : `Integer`  
    盔甲栏序号，范围0-3
  - item : `Item`  
    盔甲栏中的物品对象

- 拦截事件：不可以拦截

<br>

#### `"onUseRespawnAnchor"` - 玩家使用重生锚

- 监听函数原型
  `function(player,pos)`
- 参数：
  - player : `Player`  
    使用重生锚的玩家指针
  - pos : `IntPos`  
    被使用的重生锚的位置
- 拦截事件：函数返回`false`

<br>

### 实体相关事件

#### `"onMobDie"` - 生物死亡（包括玩家）
- 监听函数原型
`function(mob,source)`
- 参数：
    - mob : `Entity`  
      死亡的实体对象

    - source : `Entity`  
      伤害来源的实体对象

- 拦截事件：函数返回`false`

<br>

#### `"onMobHurt"` - 生物受伤（包括玩家）
- 监听函数原型
`function(mob,source)`
- 参数：
    - mob : `Entity`  
      受伤的实体对象

    - source : `Entity`  
      伤害来源的实体对象

- 拦截事件：函数返回`false`

<br>

#### `"onExplode"` - 发生爆炸
- 监听函数原型
`function(source,pos)`
- 参数：
    - source : `Entity`  
      爆炸来源的实体对象

    - pos : `FloatPos`  
      爆炸发生的坐标

- 拦截事件：函数返回`false`

<br>

### 方块相关事件

#### `"onBlockExploded"` - 方块被爆炸破坏

- 监听函数原型
  `function(block,pos,source)`
- 参数：
  - block : `Block`  
    被爆炸破坏的方块对象
  - pos : `IntPos`  
    被爆炸破坏的方块坐标
  - source : `Entity`  
    爆炸来源的实体对象
- 拦截事件：不可以拦截

<br>

#### `"onCmdBlockExecute"` - 命令方块执行命令
- 监听函数原型
`function(cmd,pos)`
- 参数：
    - cmd : `String`  
      执行的命令

    - pos : `IntPos`  
      执行命令的命令方块坐标

- 拦截事件：函数返回`false`

<br>

#### `"onProjectileHit"` - 方块被弹射物击中

- 监听函数原型
  `function(block,pos,source)`
- 参数：
  - block : `Block`  
    被击中的方块对象
  - pos : `IntPos`  
    被击中的方块坐标
  - source : `Entity`  
    弹射物来源的实体对象
- 拦截事件：不可以拦截

<br>

#### `"onProjectileHit"` - 方块被弹射物击中

- 监听函数原型
  `function(block,pos,source)`
- 参数：
  - block : `Block`  
    被击中的方块对象
  - pos : `IntPos`  
    被击中的方块坐标
  - source : `Entity`  
    弹射物来源的实体对象
- 拦截事件：不可以拦截

<br>

#### `"onHopperSearchItem"` - 漏斗检测可否吸取物品

<br>

#### `"onPistonPush"` - 活塞推动

- 监听函数原型
  `function(pistonPos,block)`
- 参数：
  - pistonPos : `IntPos`  
    正在工作的活塞坐标
  - block : `Block`  
    被推动的方块对象
- 拦截事件：函数返回`false`

<br>

#### `"onFarmLandDecay"` - 耕地退化

- 监听函数原型
  `function(pos,entity)`
- 参数：
  - pos : `IntPos`  
    退化的耕地的坐标
  - entity : `Entity`  
    造成耕地退化的实体
- 拦截事件：函数返回`false`

<br>

### 其他事件

#### `"onScoreChanged"` - 计分板数值改变

- 监听函数原型
  `function()`
- 参数：
  - 无
- 拦截事件：不可以拦截

<br>

#### `"onServerStarted"` - 服务器启动完毕
- 监听函数原型
`function()`
- 参数：
    - 无
- 拦截事件：不可以拦截

<br>

#### `"onServerCmd"` - 服务端执行后台命令
- 监听函数原型
`function(cmd)`
- 参数：
    - cmd : `String`  
      执行的后台命令

- 拦截事件：函数返回`false`

<br>

[<< 返回目录](README.md)