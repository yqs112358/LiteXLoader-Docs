# LiteXLoader - 实体 API
> 对于实体对象，除了可以使用 **通用API** 之外，还有这些额外的功能  

## 实体 API

### 获取实体名称  
`getName(entity)`
- 参数：
    1. entity : `Pointer`  
    待查询的实体指针  
- 返回值：目标实体的名称
- 返回值类型： `String` 
    - 如返回值为 `Null` 则表示获取名称失败  
<br>

### 获取实体坐标  
`getPos(entity)`
- 参数：
    1. entity : `Pointer`  
    待查询的实体指针  
- 返回值：目标实体的位置
- 返回值类型：`FloatPos` 
    - 如返回值为 `Null` 则表示获取位置失败  
<br>

### 传送实体至指定位置  
`teleport(entity,pos)`
- 参数：
    1. entity : `Pointer`  
    实体指针
    2. pos : `FloatPos`  
    目标位置坐标
- 返回值：是否成功传送
- 返回值类型：`Boolean`   
<br>

### 杀死指定实体  
`kill(entity,pos)`
- 参数：
    1. entity : `Pointer`  
    实体指针  
- 返回值：是否成功执行
- 返回值类型：`Boolean`   
<br>