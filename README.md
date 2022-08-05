**概述**

DOAF 是用于创建基于Azure云的企业应用的完整框架！遵循最佳实践和约定，为你提供强大的Azure云原生集成能力。

**开始**

[快速入门](url)是一个由单部分组成的快速入门教程。如果您想快速启动 DOAF，请从本教程开始。

**项目框架结构**

DOAF 的分层结合了领域的概念。

框架分为 4 个部分：

    1、平台：
        存放位置：00.Platform/Packages
        包含框架基础依赖包和可选功能包。自由搭配选择这些包可实现包括轻松对接Azure资源、对接常用中间件、消息推送、流水号生成等功能

    2、模块（领域）：
        存放位置：01.Modules
        包含：
        框架内置模块：基本的项目业务实现,包括用户、组织、系统配置
        业务模块：项目的业务实现

    3、项目入口
       Main函数的所在位置。项目以什么形式发布，如何Hosing，配置文件存放等都在这一层处理

    4、单元测试部分：暂未完善

**平台**

    Medalsoft.Core 为核心依赖包，开发DOAF项目必须引用。包含绝大部分公共接口（interface）和实体（entity），此外还存放了少量基础的工具代码。

    引入扩展库的命名规范为：MedalSoft.[第三方库名称]，示例：第三方库名称为：CsRedis，扩展库名称为：Medalsoft.CsRedis

[日志](url)

    日志模块暂时将serilog作为唯一日志扩展，更多关于日志扩展信息请移步至框架规划
    现有项目：
    Medalsoft.Log

[数据访问](url)

    现在绝大部分项目都是基于某个ORM（关系映射）进行开发，提供了对应的仓储接口，开发者可以自行扩展。DOAF 使用SqlSugar作为默认ORM
    现有项目：
        Medalsoft.SqlSugar
        Medalsoft.Dapper

[定时任务和后台任务](url)：

由于定时任务和后台任务，.net core 3.1 之后已经有提供接口 BackgroundService ，DOAF 实现了一种相对简洁的后台服务。

        Medalsoft.Hangfire

[缓存](url)：

    Medalsoft.Cache 为缓存基础库，为第三方库接入DOAF提供扩展标准，默认使用 MemoryCache。
        已接入的缓存扩展：
        Medalsoft.CsRedis
        Medalsoft.FreeRedis

[Azure](url)：

    现有以下二次封装库：
        Medalsoft.AzureADB2C
        Medalsoft.AzureStorage
        Medalsoft.SharePointCsom
        Medalsoft.GraphApi

[业务相关扩展](url)

    为了更好的支持项目开发，避免一些不必要的重复工作，将部分高度重复可用，且有一定扩展需求的功能进行了扩展封装，这些库里面有部分是允许或必须自行实现接口（interface），以保证最贴近项目需求。
    现有项目：
        Medalsoft.SerialNumber
        Medalsoft.Page
        Medalsoft.MessageCore
        Medalsoft.Document

[开发体验相关扩展](url)

    为了更好的支持项目开发体验，避免一些不必要的重复工作。将引入一些提高工作效率以及沟通的工具。
    现有项目：
        Medalsoft.Swagger

**模块**

[项目模块](url)
    
    项目与项目之间有部分相似，甚至相同的功能，但又由于每个项目都有自定义的可能，并且会进行模块间的交互。MedalSoft Framework 中将这部分内容分为基础的4个模块：
        Medalsoft.Common
        Medalsoft.ProjectCore
        Medalsoft.ServiceContract
        Medalsoft.System

**入口**

[项目模块](url)
    
    每个项目有不同的需求以及技术难度和工作量，为了更好的适配相应项目的需求，DOAF 中将这部分内容分为基础的3个项目：
        Medalsoft.FullSample：适合高度自定义的项目
        Medalsoft.MinimalAPI：适合微小型项目（只需要几个接口或者只是做为中转程序）
        Medalsoft.Sample：大部分项目