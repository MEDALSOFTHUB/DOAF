**Overview**

DOAF is a complete framework for creating Azure cloud-based enterprise applications! Follow best practices and conventions to provide you with powerful Azure cloud-native integration capabilities.

**start**

[Quickstart](url) is a one-part quickstart tutorial. If you want a quick start to DOAF, start with this tutorial.

**Project Framework**

The layers of DOAF combine the concept of domains.

The framework is divided into 4 parts:

    1. Platform:
        Storage location: 00.Platform/Packages
        Contains framework basic dependency packages and optional feature packages. These packages can be freely matched and selected to realize functions including easy connection to Azure resources, connection to common middleware, message push, serial number generation, etc.

    2. Modules (fields):
        Storage location: 01.Modules
        Include:
        Framework built-in modules: basic project business implementation, including user, organization, system configuration
        Business module: business realization of the project

    3. Project entry
       The location of the Main function. In what form the project is released, how to Hosing, and the storage of configuration files are all handled at this layer.

    4. Unit testing part: not yet perfect

**platform**

    Medalsoft.Core is the core dependency package, which must be referenced when developing DOAF projects. It contains most of the public interfaces and entities, and also stores a small amount of basic tool code.

    The naming convention of the imported extension library is: MedalSoft.[name of the third-party library], for example: the name of the third-party library is: CsRedis, and the name of the extension library is: Medalsoft.CsRedis

[log](url)

    The log module temporarily uses serilog as the only log extension. For more information about log extensions, please go to Framework Planning
    Existing projects:
    Medalsoft.Log

[data access](url)

    At present, most projects are developed based on an ORM (relational mapping), which provides a corresponding repository interface, and developers can expand it by themselves. DOAF uses SqlSugar as default ORM
    Existing projects:
        Medalsoft.SqlSugar
        Medalsoft.Dapper

[Scheduled tasks and background tasks] (url):

Due to timed tasks and background tasks, the interface BackgroundService has been provided since .net core 3.1, and DOAF implements a relatively simple background service.

        Medalsoft.Hangfire

[cache](url):

    Medalsoft.Cache is the basic cache library and provides extended standards for third-party libraries to access DOAF. MemoryCache is used by default.
        Accessed cache extensions:
        Medalsoft.CsRedis
        Medalsoft.FreeRedis

[Azure](url):

    The following secondary packaging libraries are available:
        Medalsoft.AzureADB2C
        Medalsoft.AzureStorage
        Medalsoft.SharePointCsom
        Medalsoft.GraphApi

[Business related extension](url)

    In order to better support project development and avoid some unnecessary duplication of work, some functions that are highly repeatable and available and have certain expansion requirements have been expanded and encapsulated. Some of these libraries are allowed or must implement their own interfaces (interface), In order to ensure that it is closest to the project needs.
    Existing projects:
        Medalsoft.SerialNumber
        Medalsoft.Page
        Medalsoft.MessageCore
        Medalsoft.Document

[Development experience related extensions](url)

    In order to better support the project development experience, avoid unnecessary duplication of work. Some tools will be introduced to improve productivity as well as communication.
    Existing projects:
        Medalsoft.Swagger

**Module**

[project module](url)
    
    There are some similarities between projects and even the same functions, but because each project has the possibility of customization and interaction between modules. This part of the MedalSoft Framework is divided into four basic modules:
        Medalsoft.Common
        Medalsoft.ProjectCore
        Medalsoft.ServiceContract
        Medalsoft.System

**Entrance**

[project module](url)
    
    Each project has different requirements, technical difficulty and workload. In order to better adapt to the needs of the corresponding project, DOAF divides this part of the content into three basic projects:
        Medalsoft.FullSample: suitable for highly customized projects
        Medalsoft.MinimalAPI: suitable for small and small projects (only need a few interfaces or just as a transfer program)
        Medalsoft.Sample: Most items
