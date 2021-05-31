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

  - [游戏接口文档 - Game API](GameApi.md)  
    通用接口模块：注册命令、操作游戏元素等
    
  - [事件监听文档 - Event API](EventApi.md)  
    事件接口模块：响应游戏事件并做出相应的反应
  
  - [GUI表单界面文档 - GUI API](GuiApi.md)  
    可视化模块：操作和构建游戏内 GUI 表单
    
  - [NBT文档 - NBT API](NbtApi.md)  
    NBT模块：操作 NBT 数据
  
- 脚本强化接口

  - [脚本辅助文档 - Script API](ScriptApi.md)  
    辅助接口模块：重要辅助功能，包括日志功能、异步接口等
    
  - [系统功能接口文档 - System API](SystemApi.md)  
    系统功能模块：对接底层系统接口，包括操作文件系统、访问网络等
  
  - [数据库与配置文件文档 - DB API](DBApi.md)  
    数据处理模块：处理大量数据，包括操作数据库、配置文件、经济系统等

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