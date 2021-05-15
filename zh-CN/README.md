# LiteXLoader - 划时代 x 跨语言脚本插件加载器

## 🎨 简介
`LiteXLoader`是一个基岩版官方服务端`Bedrock Delicated Server`（以下简称**BDS**）的插件框架，提供强大的跨语言脚本插件支持能力和稳定的开发API支持。  

## ⛳设计思想

### 模块化

`LiteXLoader`基于模块化的设计思想，将底层加载器接口、多种脚本引擎后端、插件加载模块互相分离，保证各个部分可以单独维护升级，同时又可以很好地协同工作。

### 跨语言

`LiteXLoader`为各种脚本语言提供统一的API接口，一份文档就可以涵盖所有的API接口实现，一目了然。

### 面向对象

为了开发的方便和体系的完善，将绝大部分API封装进`对象`中供脚本使用，这样可以很好地减少命名冲突，也让整个体系看起来更加干净。

## 📕 开发目录

> 这里是开发文档 API 的索引目录

- [通用接口文档 - BaseAPI](BaseAPI.md)

  介绍了文档阅读必备的各种**基础数据类型**还有**API文档描述约定**

  提供**命令注册**和**脚本辅助**函数等基础能力

- 游戏相关

  - [玩家文档 - PlayerAPI](PlayerAPI.md)

    提供操作**玩家**信息的能力

  - [实体文档 - EntityAPI](EntityAPI.md)

    提供操作**实体**信息的能力

  - [方块文档 - BlockAPI](BlockAPI.md)

    提供操作**方块**信息的能力

  - [物品文档 - ItemAPI](ItemAPI.md)

    提供操作**物品栏物品**信息的能力

  - [事件监听文档 - EventAPI](EventAPI.md)

    提供**响应游戏事件**的能力

  - [GUI表单界面文档 - GUIAPI](GUIAPI.md)

    提供操作和构建游戏内**GUI表单**的能力

  - [NBT文档 - NBTAPI](NBTAPI.md)

    提供操作**NBT**数据类型的能力

- 脚本辅助

  - [文件系统文档 - FileSystemAPI](FileSystemAPI.md)

    提供操作**文件系统**和部分**系统调用**的能力

  - [网络文档 - NetworkAPI](NetworkAPI.md)

    提供基础的**网络**能力

  - [数据库与配置文件文档 - DBAPI](DBAPI.md)

    提供操作**数据库**与**配置文件**的能力

