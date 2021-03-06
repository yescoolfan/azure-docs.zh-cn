---
title: "使用 Visual Studio 开发 Azure Functions | Microsoft Docs"
description: "了解如何使用用于 Visual Studio 2017 的 Azure Functions 工具开发和测试 Azure Functions。"
services: functions
documentationcenter: .net
author: ggailey777
manager: erikre
editor: 
ms.service: functions
ms.workload: na
ms.tgt_pltfrm: dotnet
ms.devlang: na
ms.topic: article
ms.date: 07/13/2017
ms.author: glenga, donnam
ms.translationtype: HT
ms.sourcegitcommit: c30998a77071242d985737e55a7dc2c0bf70b947
ms.openlocfilehash: fab2b3042faf870fe4b9d09d5e96dadb7155c450
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="azure-functions-tools-for-visual-studio"></a>用于 Visual Studio 的 Azure Functions 工具  

用于 Visual Studio 2017 的 Azure Functions 工具是 Visual Studio 的一个扩展，可用于开发、测试 C# 函数并将其部署到 Azure。 如果这是你第一次体验 Azure Functions，可以在 [Azure Functions 简介](functions-overview.md)中了解详细信息。

Azure Functions 工具提供以下优势： 

* 在本地开发计算机上编辑、生成和运行函数。 
* 将 Azure Functions 项目直接发布到 Azure。 
* 使用 Web 作业属性在 C# 代码中直接声明函数绑定，而无需单独维护绑定定义的 function.json。
* 开发和部署预先编译的 C# 函数。 与基于 C# 脚本的函数相比，预先编译的函数的冷启动性能更好。 
* 可以在 C# 中编写函数的代码，同时利用 Visual Studio 开发环境的所有优势。 

本主题介绍如何使用用于 Visual Studio 2017 的 Azure Functions 工具在 C# 中开发函数。 此外，还介绍如何将项目作为 .NET 程序集发布到 Azure。

## <a name="prerequisites"></a>先决条件

在安装 Azure Functions 工具之前，必须事先安装 [Visual Studio 2017 预览版 15.3](https://www.visualstudio.com/vs/preview/)，包括以下工作负荷之一：

* Azure 开发
* ASP.NET 和 Web 开发

若要创建和部署函数，还需要：

* 一个有效的 Azure 订阅。 如果没有 Azure 订阅，可以使用[免费帐户](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)。

* 一个 Azure 存储帐户。 若要创建存储帐户，请参阅[创建存储帐户](../storage/storage-create-storage-account.md#create-a-storage-account)。  

## <a name="install-the-azure-functions-tools"></a>安装 Azure Functions 工具

可以[下载并安装扩展包](https://marketplace.visualstudio.com/vsgallery/e3705d94-7cc3-4b79-ba7b-f43f30774d28)，或使用以下步骤从 Visual Studio 安装该包。  

[!INCLUDE [Install the Azure Functions Tools for Visual Studio](../../includes/functions-install-vstools.md)] 


## <a name="create-an-azure-functions-project"></a>创建 Azure Functions 项目 

[!INCLUDE [Create a project using the Azure Functions](../../includes/functions-vstools-create.md)]


## <a name="configure-the-project-for-local-development"></a>为本地开发配置项目

使用 Azure Functions 模板创建新项目时，将会获得一个包含以下文件的空 C# 项目：

* **host.json**：用于配置 Functions 主机。 在本地和 Azure 中运行时，都会应用这些设置。 有关详细信息，请参阅 [host.json](https://github.com/Azure/azure-webjobs-sdk-script/wiki/host.json) 参考文章。
    
* **local.settings.json**：维护本地运行函数时使用的设置。 Azure 不使用这些设置，它们由 [Azure Functions 核心工具](functions-run-local.md)使用。 使用此文件可以在其他 Azure 服务中指定设置（例如连接字符串）。 针对项目中的函数所需的每个连接，请将新键添加到 **Values** 数组。 有关详细信息，请参阅 Azure Functions 核心工具主题中的[本地设置文件](functions-run-local.md#local-settings-file)。

Functions 运行时在内部使用 Azure 存储帐户。 对于除 HTTP 和 Webhook 以外的所有触发器类型，必须将 **Values.AzureWebJobsStorage** 键设置为有效的 Azure 存储帐户连接字符串。

[!INCLUDE [Note to not use local storage](../../includes/functions-local-settings-note.md)]

 若要设置存储帐户连接字符串，请执行以下操作：

1. 在 Visual Studio 中，打开“Cloud Explorer”，展开“存储帐户” > “你的存储帐户”，然后选择“属性面板”并复制“主连接字符串”值。   

2. 在项目内，打开 local.settings.json 项目文件，并将“AzureWebJobsStorage”键的值设置为复制的连接字符串。

3. 重复上述步骤，将唯一键添加到函数所需的其他任何连接的 **Values** 数组。  

## <a name="create-a-function"></a>创建函数

在预先编译的函数中，可以通过在代码中应用属性来定义函数使用的绑定。 使用 Azure Functions 工具通过提供的模板创建函数时，系统会自动应用这些属性。 

1. 在“解决方案资源管理器”中，右键单击项目节点，然后选择“添加” > “新建项”。 选择“Azure 函数”，键入类的**名称**，然后单击“添加”。

2. 选择你的触发器，设置绑定属性，然后单击“创建”。 以下示例显示创建队列存储触发的函数时的设置。 

    ![](./media/functions-develop-vs/functions-vstools-create-queuetrigger.png)
    
    已提供名为 **QueueStorage** 的连接字符串键，该键在 local.settings.json 文件中定义。 
 
3. 检查新添加的类。 将会看到一个静态 **Run** 方法，它已使用 **FunctionName** 属性设置了属性。 该属性指示该方法是函数的入口点。 

    例如，以下 C# 类表示一个基本的队列存储触发的函数：

    ````csharp
    using System;
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Host;
    
    namespace FunctionApp1
    {
        public static class Function1
        {
            [FunctionName("QueueTriggerCSharp")]        
            public static void Run([QueueTrigger("myqueue-items", Connection = "QueueStorage")]string myQueueItem, TraceWriter log)
            {
                log.Info($"C# Queue trigger function processed: {myQueueItem}");
            }
        }
    } 
    ````
 
    已向提供给入口点方法的每个绑定参数提供了特定于绑定的属性。 该属性采用绑定信息作为参数。 在上面的示例中，第一个参数应用了 **QueueTrigger** 属性，表示队列触发的函数。 队列名称和连接字符串设置名称作为参数传递。  

## <a name="testing-functions"></a>测试函数

Azure Functions Core Tools 允许在本地开发计算机上运行 Azure Functions 项目。 首次从 Visual Studio 启动某个函数时，系统会提示你安装这些工具。  

若要测试函数，请按 F5。 如果系统提示，请按 Visual Studio 的请求下载和安装 Azure Functions Core (CLI) 工具。  可能还需启用一个防火墙例外，以便这些工具能够处理 HTTP 请求。

在运行项目时，可以像测试已部署的函数一样测试代码。 有关详细信息，请参阅[在 Azure Functions 中测试代码的策略](functions-test-a-function.md)。 在调试模式下运行时，断点将按预期命中 Visual Studio。 

有关如何测试队列触发的函数的示例，请参阅[队列触发的函数快速入门教程](functions-create-storage-queue-triggered-function.md#test-the-function)。  

若要详细了解如何使用 Azure Functions 核心工具，请参阅[在本地编写 Azure 函数代码并对其进行测试](functions-run-local.md)。

## <a name="publish-to-azure"></a>发布到 Azure

[!INCLUDE [Publish the project to Azure](../../includes/functions-vstools-publish.md)]

>[!NOTE]  
>还必须将在 local.settings.json 中添加的任何设置添加到 Azure 函数应用中。 这些设置不会自动添加。 可通过以下方式的其中一种将所需设置添加到函数应用中：
>
>* [使用 Azure 门户](functions-how-to-use-azure-function-app-settings.md#settings)。
>* [使用 `--publish-local-settings` 发布 Azure Functions Core Tools 中的选项](functions-run-local.md#publish)。
>* [使用 Azure CLI](/cli/azure/functionapp/config/appsettings#set)。 

## <a name="next-steps"></a>后续步骤

有关 Azure Functions 工具的详细信息，请参阅 [Visual Studio 2017 Tools for Azure Functions](https://blogs.msdn.microsoft.com/webdev/2017/05/10/azure-function-tools-for-visual-studio-2017/)（用于 Azure Functions 的 Visual Studio 2017 工具）博客文章中的“Common Questions”（常见问题）部分。

若要详细了解 Azure Functions 核心工具，请参阅[在本地编写 Azure 函数代码并对其进行测试](functions-run-local.md)。  
若要详细了解如何将函数作为 .NET 类库进行开发，请参阅[搭配使用 Azure Functions 和 .Net 类库](functions-dotnet-class-library.md)。 本主题还举例说明了如何使用属性来声明 Azure Functions 支持的各种类型的绑定。    

