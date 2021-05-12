# LiteXLoader - 方块 API
> 除了通用API之外，还有些在处理方块相关事务时需要额外使用到的 API  

### 获取方块名称  
`getName(block)`
- 参数：
    1. block : `Pointer`  
    待查询的方块指针  
- 返回值：目标方块的名称
- 返回值类型： `String` 
    - 如返回值为 `Null` 则表示获取名称失败  
<br>