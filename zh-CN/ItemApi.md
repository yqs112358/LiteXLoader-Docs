# LiteXLoader - 物品 API
> 对于物品对象，除了可以使用 **通用API** 之外，还有这些额外的功能  

### 获取物品名称  
`getName(item)`
- 参数：
    1. item : `Pointer`  
    待查询的物品指针  
- 返回值：目标物品的名称
- 返回值类型： `String` 
    - 如返回值为 `Null` 则表示获取名称失败  
<br>

### 获取物品的自定义名称
`getCustomName(item)`
- 参数：
    1. item : `item`  
    物品指针
- 返回值：目标物品的自定义名称（游戏内实际显示的名字）
- 返回值类型： `String` 
    - 如返回值为 `Null` 则表示获取名字失败 
<br>

### 获取物品堆叠的个数
`getCount(item)`
- 参数：
    1. item : `item`  
    物品指针
- 返回值：目标物品堆叠的个数
- 返回值类型： `Number`
<br>

### 设置自定义Lore
`setLore(item,names)`
- 参数：
    1. item : `item`  
    物品指针
    2. names : `Array<String,String,...>`  
    要设置成的Lore字符串的数组
- 返回值：是否设置成功
- 返回值类型： `Boolean`
<br>