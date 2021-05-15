# LiteXLoader - GUI API

[<< 返回目录](README.md)

> 这里是一些在游戏中创建、修改或者影响**GUI界面**时会用到的函数。  
> 所有GUI相关的接口都被封装进 mc 对象中  

## 表单相关 API

### 向玩家发送简单表单  
`mc.sendSimpleForm(player,title,content,buttons,callback)`

- 参数：

    - player : `Player`  
      目标玩家对象

    - title : `String`  
      表单标题  

    - content : `String`  
      表单内容

    - buttons : `Array<String,String,...>`  
      各个按钮文本的字符串数组  

    - callback : `Function`  
      玩家选择按钮之后被调用的回调函数。  
      函数原型：

- 返回值：发送的表单ID  

- 返回值类型：`Integer`

<br>

### 向玩家发送模式对话框  
`mc.sendModelForm(player,title,content,button1,button2,callback)`

- 参数：
    - player : `Player`  
      目标玩家对象

    - title : `String`  
      表单标题  

    - content : `String`  
      表单内容

    - button1 : `String`  
      按钮1文本的字符串  

    - button2 : `String`  
      按钮2文本的字符串  

    - callback : `Function`  
      玩家选择按钮之后被调用的回调函数。  
      函数原型：

- 返回值：发送的表单ID  

- 返回值类型：`Integer`

<br>

### 向玩家发送自定义表单（Json格式）  
`mc.sendModelForm(player,json,callback)`

- 参数：
    - player : `Player`  
      目标玩家对象

    - json : `String`  
      自定义表单json字符串  

    - callback : `Function`  
      玩家与表单元素互动之后被调用的回调函数。  
      函数原型：

- 返回值：发送的表单ID  

- 返回值类型：`Integer`  

<br>

### 取消之前发送的表单  
`mc.giveUpForm(id)`

- 参数：
    - id : `Integer`  
      上述这些函数返回的表单ID

- 返回值：是否成功取消  

- 返回值类型：`Boolean`  

<br>

## 表单协助 API
> 这些API可以协助开发者方便地构造一个自定义表单，不再需要为编写Json麻烦而头疼

LXL提供了**表单对象**来方便地创建一个表单并发送至指定玩家。

### 创建表单对象

在使用这些API之前，你需要先用这个函数创建一个空白的表单对象

`mc.createForm()`

- 返回值：新创建的空白表单对象
- 返回值类型：`Form`

<br>

### 添加表单元素

创建完之后，你就可以用下面这些成员函数（成员方法）向对象中增加新的表单元素。对于某个特定的表单对象`fm`，有以下这些函数

#### 向表单内增加一行文本  
`fm.addLabel(text)`

- 参数：
    - text : `String`  
      一行文本
- 返回值：无 

<br>

#### 向表单内增加一行输入框  
`fm.addInput(title,placeholder)`
- 参数：

    - title : `String`  
      输入框描述文本

    - placeholder : `String`  
      输入框内的提示字符
- 返回值：无 

<br>

#### 向表单内增加一行开关选项  
`fm.addSwitch(title)`

- 参数：
    - title : `String`  
      开关选项描述文本
- 返回值：无 

<br>

#### 向表单内增加一行下拉菜单  
`fm.addDropdown(title,items[,default])`
- 参数：

    - title : `String`  
      下拉菜单描述文本

    - items : `Array<String,String,...>`  
      下拉菜单中的选项文本列表

    - default(可选参数) : `Integer`  
      下拉菜单默认选中的列表项序号。序号从0开始编号  
      默认为0，即选中列表的第一项
- 返回值：无 

<br>

#### 向表单内增加一行游标滑块  
`fm.addSlider(title,length,default)`
- 参数：
    - title : `String`  
      游标滑块描述文本

    - length : `Integer`  
      游标滑块最大格数

    - default(可选参数) : `Integer`  
      游标滑块默认初始格数。  
        默认为0，即处于滑块行的开头
- 返回值：无 

<br>

#### 向表单内增加一行步进滑块  
`fm.addStepSlider(title,items[,default])`

- 参数：
    - title : `String`  
      步进滑块描述文本

    - items : `Array<String,String,...>`  
      步进滑块的选项文本列表

    - default(可选参数) : `Integer`  
      步进滑块默认初始选项。序号从0开始编号  
      默认为0，即选中滑块的第一项
- 返回值：无 

<br>

### 发送表单

最后，在一切就绪之后，你就可以用这个函数将配置好的表单对象发送给玩家，并监听玩家的互动消息

`fm.send(player,callback)`

- 参数：
    - player : `Player`  
      目标玩家对象

    - callback : `Function`  
      玩家与表单元素互动之后被调用的回调函数。  
      函数原型：
- 返回值：发送的表单ID  
- 返回值类型：`Integer`

> 表单对象可以被反复发送，每次发送都会使用一个不同的表单ID，并在互动时调用各自设置好的回调函数，不会打架。

被发送出去的表单同样可以用之前提到的API撤销，传入send函数返回的表单ID即可。

<br>