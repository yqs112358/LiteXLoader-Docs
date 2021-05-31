# LiteXLoader - 数据库与配置文件文档 

[<< 返回目录](README.md)

配置文件和数据库是插件开发过程中非常重要的组成部分。在插件工作过程中，难免会碰到需要处理配置和大量游戏相关数据的场景。  
LXL为脚本插件提供了大量**基础设施**，包括配置文件、数据库、经济系统等。  
方便开发者专注于业务代码实现，而非纠结于这些方面的技术细节。  

<br>

## 配置文件 API

配置文件，一般用于将插件的某些可供用户修改的设置项独立成文件，以方便修改某些设置。  
因此，配置文件的内容和格式一般需要有一定的可读性。  
LXL提供统一配置文件接口来完成这个任务。  
当然，你也可以手动读写文件来协助相关配置文件的操作。  

### 初始化配置文件模块

在使用内置的配置文件接口之前，LXL需要初始化相关的配置。  
传入插件的名字（和可选的配置文件类型）之后，如果目标文件不存在，引擎将在 `BDS根目录/plugins/插件名字/` 目录下建立名为`config.json`或`config.ini`的配置文件。  
配置文件类型默认为`json`，当然你也可以修改为`ini`格式。

`conf.init(name[,format,default])`

- 参数：
  - name : `String`  
    你的插件名字，引擎根据名字创建配置文件目录
  - format : `String`  
    （可选参数）配置文件的格式，字符串形式。可选项有 `json ` 或 ` ini`   
    如果不传入此参数，默认为 `json` 格式
  - default : `String`  
    （可选参数）配置文件的默认内容。  
    如果初始化时配置文件**不存在**，引擎将新建文件并将此处的默认内容写入文件中。  
    如果不传入此参数，新建时的配置文件将为空
- 返回值：是否初始化成功
- 返回值类型：`Boolean`

注：配置文件格式的选择将影响你可以储存的配置数据类型。  
json格式可以储存**绝大多数**类型的数据，包括数组、对象等；  
ini格式相对**简单直观**，他人修改起来比较轻松，不过储存的数据类型受到一定限制

统一配置文件初始化完毕之后，就可以使用API接口方便地读写。

<br>

### Json 格式：读写配置文件

如果配置文件选择的是`Json`格式，你有这些读写接口可用

#### 写入配置项

`conf.set(name,data)`

- 参数：
  - name : `String`  
    配置项名字
  - data : `任意类型`  
    要写入的配置数据。允许的配置数据类型有：  
    `Integer` `Float` `String` `Boolean` `Array` `Object`  
    其中，`Array` 和 `Object` 内部仅能嵌套上面这些元素

- 返回值：是否写入成功

- 返回值类型：`Boolean`

<br>

#### 读取配置项

`conf.get(name[,default])`

- 参数：
  - name : `String`  
    配置项名字
  - default : `任意类型`  
    （可选参数）当读取失败时的返回值  
    默认为`Null`
- 返回值：指定配置项的数据
- 返回值类型：`任意类型`，以具体储存的数据类型为准

<br>

#### 删除配置项

`conf.delete(name)`

- 参数：
  - name : `String`  
    配置项名字
- 返回值：是否写入成功
- 返回值类型：`Boolean`

如果这个配置项你不需要了，为了避免在他人修改配置文件时引起迷惑，你可以选择将它删除

<br>

### Ini 格式：读写配置文件

如果配置文件选择的是`ini`格式，你有这些读写接口可用

#### 写入配置项

`conf.setKey(section,name,data)`

- 参数：
  - section : `String`  
    配置项键名
  - name : `String`  
    配置项名字
  - data : `任意类型`  
    要写入的配置数据。允许的配置数据类型有：  
    `Integer` `Float` `String` `Boolean`

- 返回值：是否写入成功

- 返回值类型：`Boolean`

如果配置项不存在，接口会自动创建

<br>

#### 读取整数项

`conf.getInt(section,name[,default])`

- 参数：
  - section : `String`  
    配置项键名
  - name : `String`  
    配置项名字
  - default : `Integer`  
    （可选参数）当读取失败时的返回值  
    默认为`0`
- 返回值：指定配置项的数据
- 返回值类型：`Integer`

<br>

#### 读取字符串项

`conf.getStr(section,name[,default])`

- 参数：
  - section : `String`  
    配置项键名
  - name : `String`  
    配置项名字
  - default : `String`  
    （可选参数）当读取失败时的返回值  
    默认为`""`
- 返回值：指定配置项的数据
- 返回值类型：`String`

<br>

#### 读取浮点数项

`conf.getFloat(section,name[,default])`

- 参数：
  - section : `String`  
    配置项键名
  - name : `String`  
    配置项名字
  - default : `Float`  
    （可选参数）当读取失败时的返回值  
    默认为`0.0`
- 返回值：指定配置项的数据
- 返回值类型：`Float`

<br>

#### 读取布尔项

`conf.getBool(section,name[,default])`

- 参数：
  - section : `String`  
    配置项键名
  - name : `String`  
    配置项名字
  - default : `Boolean`  
    （可选参数）当读取失败时的返回值  
    默认为`false`
- 返回值：指定配置项的数据
- 返回值类型：`Boolean`

<br>

#### 删除配置键

`conf.deleteSec(section)`

- 参数：
  - section : `String`  
    配置项键名
- 返回值：是否删除成功
- 返回值类型：`Boolean`

如果这个配置键你不需要了，你可以将它整个删除

<br>

#### 删除配置项

`conf.deleteKey(section,name)`

- 参数：
  - section : `String`  
    配置项键名
  - name : `String`  
    配置项名字
- 返回值：是否删除成功
- 返回值类型：`Boolean`

如果这个配置项你不需要了，为了避免在他人修改配置文件时引起迷惑，你可以选择将它删除

<br>

### 其他的通用接口函数

此处是一些辅助用途的的通用的接口函数

#### 重新加载文件中的配置项

`conf.reload()`

- 返回值：无

为了性能考虑，统一配置文件接口对读操作进行缓存，每次读取操作都从直接内存中读取，而写入才会直接写入磁盘文件。考虑到配置文件可能被用户修改，当你确认用户已经修改配置文件之后，需要使用此函数刷新统一配置文件的内存缓存数据。

<br>

#### 获取配置文件路径

`conf.getPath()`

- 返回值：当前配置文件的文件路径
- 返回值类型：`String`

<br>

#### 读取整个配置文件的内容

`conf.read()`

- 返回值：当前配置文件的所有内容
- 返回值类型：`String`

<br>

#### 写入整个配置文件的内容

`conf.write(content)`

- 参数：
  - content : `String`  
    写入的内容
- 返回值：是否写入成功
- 返回值类型：`Boolean`

<br>

------

## 数据库 API

数据库，一般用于插件可持久化地储存某些插件所生成和处理的数据。  
不同于配置文件，数据库一般没有可读性方面的要求，而对性能和稳定性有相当的考虑。  
LXL提供统一数据库接口来完成这个任务。    
具体实现上，LXL提供了两种不同的数据库格式：键 - 值对格式的NoSQL数据库，和表格形式的SQL数据库。你可以按需使用。

### 键 - 值对 NoSQL数据库

键 - 值对数据库适用于储存键 - 值形式的数据，形如`name:apple` , `value:5`等等。  
底层使用leveldb实现

#### 创建 / 打开数据库

在使用数据库之前，你先需要给出一个数据库路径，LXL将打开/创建指定的数据库并返回一个数据库对象。  
一个leveldb数据库是由多个文件组成的，所以你需要传入一个目录的路径，数据库文件会被储存于这个目录当中。  
如果这个目录已含有一个数据库，LXL会将它打开，否则会新建一个。

`conf.openDB(dir)`

- 参数：
  - dir : `String`  
    数据库的储存目录路径
- 返回值：打开 / 创建的数据库对象
- 返回值类型：`DB`
  - 如果返回值为`Null`，则代表创建 / 打开失败

成功打开数据库后，你可以使用下面的接口来进行相关的操作。  
对于一个数据库对象`db`，有以下这些函数：

<br>

#### 写入数据项

`db.set(name,data)`

- 参数：
  - name : `String`  
    数据项名字
  - data : `任意类型`  
    要写入的数据，可以是任意类型。  
- 返回值：是否写入成功
- 返回值类型：`Boolean`

注：允许使用数据库储存的数据类型有：   
`Integer` `Float` `String` `Boolean` `Array` `Object `  
其中，`Array` 和 `Object` 内部仅能嵌套上面出现的这些元素

<br>

#### 读取数据项

`db.get(name)`

- 参数：
  - name : `String`  
    数据项名字
- 返回值：数据库中储存的这个项的数据
- 返回值类型：`任意类型`，以具体储存的数据类型为准
  - 如返回值为 `Null` 则表示数据不存在

<br>

#### 删除数据项

`db.delete(name)`

- 参数：
  - name : `String`  
    数据项名字

<br>

------

## SQL数据库

SQL数据库适用于使用SQL语句处理大量的关系型数据。接口底层使用sqlite3实现

<br>

------

## 经济系统 API

在很多服务器中，经济系统是非常关键的一环。  
为了解决传统使用计分板经济系统的种种问题，LXL提供了对接LLMoney经济系统的接口，可以与LL系列插件直接互通。  
LLMoney除了拥有传统经济系统的能力之外，还有查询金额变动历史、操作离线玩家经济等额外能力。  
当然，在使用经济系统接口前，你需要提前在LiteLoader安装好LLMoney插件。否则，这些接口都将无法正常工作。  

注意：为了可以操作离线玩家的钱包，经济系统接口统一使用Xuid来作为玩家的统一标识符，而非其他地方通用的`Player`玩家指针。对于某个玩家指针`pl`，你可以使用`pl.xuid`来获取他的xuid字符串，并将其作为参数传入。

#### 设置玩家的存款金额

`money.set(xuid,money)`

- 参数：
  - xuid : `String`  
    要操作的玩家的Xuid标识符
  - money : `Integer`  
    要设置的金额  
- 返回值：是否设置成功
- 返回值类型：`Boolean`

<br>

#### 获取玩家的存款金额

`money.get(xuid)`

- 参数：
  - xuid : `String`  
    要读取的玩家的Xuid标识符
- 返回值：玩家的资金数值
- 返回值类型：`Integer`

<br>

#### 增加玩家的存款

`money.add(xuid,money)`

- 参数：
  - xuid : `String`  
    要操作的玩家的Xuid标识符
  - money : `Integer`  
    要增加的金额  
- 返回值：是否设置成功
- 返回值类型：`Boolean`

<br>

#### 减少玩家的存款

`money.reduce(xuid,money)`

- 参数：
  - xuid : `String`  
    要操作的玩家的Xuid标识符
  - money : `Integer`  
    要减小的金额  
- 返回值：是否设置成功
- 返回值类型：`Boolean`

<br>

#### 进行一笔转账

`money.trans(xuid1,money,xuid2[,note])`

- 参数：
  - xuid1 : `String`  
    付款的玩家的Xuid标识符
  - money : `Integer`  
    要支付的金额  
  - xuid2 : `String`  
    收款的玩家的Xuid标识符
  - note : `String`  
    （可选参数）给这笔转账附加一些文字说明
- 返回值：是否转账成功
- 返回值类型：`Boolean`

<br>

#### 查账

`money.`

<br>

#### 删除账单记录

<br>

[<< 返回目录](README.md)