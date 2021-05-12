# LiteXLoader - GUI API
> 这里是一些在游戏中创建、修改或者影响界面时会用到的函数  

## 玩家相关 API

### 设置玩家自定义侧边栏计分板  
`setScoreBoard(player,title,data)`
- 参数：
    1. player : `Pointer`  
    玩家指针
    2. title : `String`  
    侧边栏标题  
    3. data : `Array<String,String,...>`  
    列表字符串数组  
- 返回值：是否成功设置
- 返回值类型：`Boolean`  
<br>

### 移除玩家自定义侧边栏计分板  
`setScoreBoard(player)`
- 参数：
    1. player : `Pointer`  
    玩家指针
- 返回值：是否成功移除
- 返回值类型：`Boolean`  
<br>

### 向玩家发送简单表单  
`sendSimpleForm(player,title,content,buttons,callback)`
- 参数：
    1. player : `Pointer`  
    玩家指针
    2. title : `String`  
    表单标题  
    3. content : `String`  
    表单内容
    4. buttons : `Array<String,String,...>`  
    各个按钮文本的字符串数组  
    5. callback : `Function`  
    玩家选择按钮之后被调用的回调函数。  
    函数原型：
- 返回值：发送的表单ID  
- 返回值类型：`Number`  
<br>

### 向玩家发送模式对话框  
`sendModelForm(player,title,content,button1,button2,callback)`
- 参数：
    1. player : `Pointer`  
    玩家指针
    2. title : `String`  
    表单标题  
    3. content : `String`  
    表单内容
    4. button1 : `String`  
    按钮1文本的字符串  
    5. button2 : `String`  
    按钮2文本的字符串  
    6. callback : `Function`  
    玩家选择按钮之后被调用的回调函数。  
    函数原型：
- 返回值：发送的表单ID  
- 返回值类型：`Number`  
<br>

### 向玩家发送自定义表单（Json格式）  
`sendModelForm(player,json,callback)`
- 参数：
    1. player : `Pointer`  
    玩家指针
    2. json : `String`  
    自定义表单json字符串  
    3. callback : `Function`  
    玩家与表单元素互动之后被调用的回调函数。  
    函数原型：
- 返回值：发送的表单ID  
- 返回值类型：`Number`  
<br>

### 取消之前发送的表单  
`giveUpForm(id)`
- 参数：
    1. id : `Number`  
    上述这些函数返回的表单ID
- 返回值：是否成功取消  
- 返回值类型：`Boolean`  
<br>

### 为玩家设置自定义Boss血条  
`setBossBar(player,title,percent)`
- 参数：
    1. player : `Pointer`  
    玩家指针
    2. title : `String`  
    自定义血条标题  
    3. percent : `Number`  
    血条中的血量百分比，范围为0~100。0为空血条，100为满
- 返回值：是否成功设置
- 返回值类型：`Boolean`  
<br>

### 移除玩家的自定义Boss血条  
`removeBossBar(player)`
- 参数：
    1. player : `Pointer`  
    玩家指针
- 返回值：是否成功移除
- 返回值类型：`Boolean`  
<br>

## 表单协助 API
> 这些函数可以协助开发者方便地构造一个自定义表单，不再需要为修改Json麻烦而头疼

### 初始化一个自定义表单指针  
`createForm()`
- 参数：
    - 无
- 返回值：新创建的表单指针
- 返回值类型：`Pointer`  
<br>

### 向表单内增加一行文本  
`addLabel(form,text)`
- 参数：
    1. form : `Pointer`  
    表单指针
    2. text : `String`  
    增加的文本
- 返回值：无 
<br>

### 向表单内增加一行输入框  
`addInput(form,title,placeholder)`
- 参数：
    1. form : `Pointer`  
    表单指针
    2. title : `String`  
    输入框描述文本
    3. placeholder : `String`  
    输入框内的提示字符
- 返回值：无 
<br>

### 向表单内增加一行开关选项  
`addSwitch(form,title)`
- 参数：
    1. form : `Pointer`  
    表单指针
    2. title : `String`  
    开关选项描述文本
- 返回值：无 
<br>

### 向表单内增加一行下拉菜单  
`addDropdown(form,title,items[,default])`
- 参数：
    1. form : `Pointer`  
    表单指针
    2. title : `String`  
    下拉菜单描述文本
    3. items : `Array<String,String,...>`  
    下拉菜单中的选项文本列表
    4. default(可选参数) : `Number`  
    下拉菜单默认选中的列表项序号，必须为整数。序号从0开始编号  
    默认为0，即选中列表的第一项
- 返回值：无 
<br>

### 向表单内增加一行游标滑块  
`addSlider(form,title,length,default)`
- 参数：
    1. form : `Pointer`  
    表单指针
    2. title : `String`  
    游标滑块描述文本
    3. length : `Number`  
    游标滑块最大格数，必须为整数
    4. default(可选参数) : `Number`  
    游标滑块默认初始格数，必须为整数。  
    默认为0，即处于滑块行的开头
- 返回值：无 
<br>

### 向表单内增加一行步进滑块  
`addStepSlider(form,title,items[,default])`
- 参数：
    1. form : `Pointer`  
    表单指针
    2. title : `String`  
    步进滑块描述文本
    3. items : `Array<String,String,...>`  
    步进滑块的选项文本列表
    4. default(可选参数) : `Number`  
    步进滑块默认初始选项，必须为整数。序号从0开始编号  
    默认为0，即选中滑块的第一项
- 返回值：无 
<br>

### 发送设计好的自定义表单  
`sendFrom(player,form,callback)`
- 参数：
    1. player : `Pointer`  
    玩家指针
    2. form : `Pointer`  
    设计好的自定义表单指针  
    3. callback : `Function`  
    玩家与表单元素互动之后被调用的回调函数。  
    函数原型：
- 返回值：发送的表单ID  
- 返回值类型：`Number`  
<br>