# LiteXLoader - LXL插件开发文档

## 🎨 简介
`LiteXLoader`（以下简称**LXL**）是一个基岩版官方服务端 `Bedrock Delicated Server`（以下简称**BDS**）的插件框架，提供强大的跨语言脚本插件支持能力和稳定的开发API支持。  

欢迎参与到LXL的插件开发中来！时刻欢迎你的创意和实践，让他们变成现实吧。

## 📕 开发目录

在接触LXL开发之前，你需要对LXL有一个成体系的认识。这里的文档，首先将帮助你建立一个大概的知识框架。

- 入门必读：[基础介绍文档 - Begining](Begining.md)

  介绍了LXL的各种「基础数据类型」还有 「API 文档描述约定」   
  注意：基础介绍文档对后续的开发过程至关重要，请务必首先 

  ## ===  仔细阅读！===

<br>

在阅读完上述基础文档之后，你就可以上手开发LXL插件了  
这里是所有 API 的索引目录，点击链接前往指定的章节，并了解这些 API 该如何使用

LXL的API大致分为两个部分：和游戏相关的API，以及用于辅助脚本开发的API。

- 游戏相关接口

  - [通用接口文档 - BaseAPI](BaseApi.md)  
    通用模块：命令注册、日志功能等通用接口
    
  - [玩家文档 - PlayerAPI](PlayerApi.md)  
    玩家模块
  
  - [实体文档 - EntityAPI](EntityApi.md)  
    实体模块
    
  - [方块文档 - BlockAPI](BlockApi.md)  
    方块模块
  
  - [物品文档 - ItemAPI](ItemApi.md)  
    物品栏物品模块
    
  - [事件监听文档 - EventAPI](EventApi.md)  
    事件模块：响应游戏事件、监听事件
  
  - [GUI表单界面文档 - GUIAPI](GUIApi.md)  
    可视化模块：操作和构建游戏内 GUI 表单
    
  - [NBT文档 - NBTAPI](NBTApi.md)  
    NBT模块：操作 NBT 数据

- 脚本辅助接口

  - [文件和系统文档 - FileSystemAPI](FileSystemApi.md)  
    文件系统模块：操作文件系统、进行部分系统调用
    
  - [网络文档 - NetworkAPI](NetworkApi.md)  
    网络模块：基础的网络接口
  
  - [数据库与配置文件文档 - DBAPI](DBApi.md)  
    数据模块：操作数据库、配置文件、内置经济系统

<br>

## 🎁 参与贡献

我们欢迎你对LiteXLoader做出自己的贡献！  
你可以通过下面这些方法来为项目做出贡献

1. 贡献代码，维护项目和符号
2. 帮助修改和优化开发文档
3. 按格式编写你想要的新API并提交PR，或者提出好的建议
4. 帮助我们宣传LXL，对我们的开发给予支持

有你们，LiteXLoader将变得更好~

#### 欢迎 star⭐ 和 PR！GitHub项目链接：[LiteXLoader](https://github.com/LiteLDev/LiteXLoader)