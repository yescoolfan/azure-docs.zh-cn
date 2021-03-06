---
title: "5 分钟内在 Azure 门户中部署 WordPress 应用 |Microsoft Docs"
description: "了解如何通过部署 WordPress 应用，轻松地在应用服务中运行 Web 应用。 将立即看到成果。"
services: app-service\web
documentationcenter: 
author: cephalin
manager: erikre
editor: 
ms.assetid: 6feac128-c728-4491-8b79-962da9a40788
ms.service: app-service-web
ms.workload: web
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: quickstart
ms.date: 02/13/2017
ms.author: cephalin
ms.custom: mvc
ms.translationtype: Human Translation
ms.sourcegitcommit: 0921b01bc930f633f39aba07b7899ad60bd6a234
ms.openlocfilehash: 7ef5802866bf96859d3f44cdb58cbb412b08a700
ms.contentlocale: zh-cn
ms.lasthandoff: 03/01/2017

---
# <a name="deploy-a-wordpress-app-in-the-azure-portal-in-five-minutes"></a>5 分钟内在 Azure 门户中部署 WordPress 应用

本教程演示了如何在几分钟内将首个 [WordPress](https://wordpress.org/) Web 应用部署到 [Azure 应用服务](../app-service/app-service-value-prop-what-is.md)。

![WordPress 站点](./media/app-service-web-get-started-php-portal/wpdashboard.png)

## <a name="prerequisites"></a>先决条件
需要一个 Microsoft Azure 帐户。 如果没有帐户，可以[注册免费试用帐户](https://azure.microsoft.com/pricing/free-trial/?WT.mc_id=A261C142F)，或者[激活 Visual Studio 订户权益](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F)。

> [!NOTE]
> 无需 Azure 帐户即可 [试用应用服务](https://azure.microsoft.com/try/app-service/) 。 创建入门级应用并使用长达一小时 — 无需信用卡，也无需做出承诺。
> 
> 

## <a name="deploy-the-wordpress-app"></a>部署 WordPress 应用
1. 登录到 [Azure 门户](https://portal.azure.com)。

2. 打开 [https://portal.azure.com/#create/WordPress.WordPress](https://portal.azure.com/#create/WordPress.WordPress)。

    此链接是立即在 Azure 门户中配置新 WordPress 应用的快捷方式。

3. 在“应用名称”中，键入 Web 应用名称。 如果该名称在 `azurewebsites.net` 域中是唯一的，则会在框中看到绿色的复选标记。
   
5. 在“资源组”中，单击“新建”创建新的[资源组](../azure-resource-manager/resource-group-overview.md)，然后为其命名。

6. 在“数据库提供程序”中，选择“CleaDB”。

7. 单击“应用服务计划/位置” > “新建”。 按以下步骤配置[应用服务计划](../app-service/azure-web-sites-web-hosting-plans-in-depth-overview.md)：

    - 在“应用服务计划”中，键入所需名称。
    - 在“位置”中，选择用于托管计划的位置。
    - 单击“定价层”，然后选择“F1 免费”或适合你的其他层，然后单击“选择”。
    - 单击 **“确定”**。

8. 单击“数据库” > “新建”。 按以下步骤配置 SQL 数据库：

    - 在“数据库名称”中，键入数据库名称。 
    - 在“位置”中，选择与应用服务计划相同的位置。
    - 单击“定价层”，然后选择“Mercury”或适合你的其他层，再单击“选择”。
    - 单击“法律条款”，然后单击“购买”。
    - 单击 **“确定”**。

9. 单击“创建” 。

    Azure 现基于你的配置创建 WordPress 应用。 将看到“部署已启动...”通知。

    ![部署已启动 - Azure 应用服务中的首个 WordPress](./media/app-service-web-get-started-php-portal/deployment-started.png)
   
## <a name="launch-and-manage-your-wordpress-web-app"></a>启动和管理你的 WordPress Web 应用

Azure 完成应用部署时，你将看到另一条通知。

![部署已成功 - Azure 应用服务中的首个 WordPress](./media/app-service-web-get-started-php-portal/deployment-succeeded.png)

1. 单击该通知。 如果错过通知，可始终通过单击通知铃声图标获取通知（![通知图标 - Azure 应用服务中的首个 WordPress](./media/app-service-web-get-started-dotnet-portal/notification.png)）。

    现在应可看到 Web 应用的管理[边栏选项卡](../azure-resource-manager/resource-group-portal.md#manage-resources)（边栏选项卡：水平打开的一个门户页面）。

3. 在“概述”页面顶部，单击“浏览”。
   
    ![浏览 - Azure 应用服务中的首个 WordPress](./media/app-service-web-get-started-php-portal/browse.png)

    现可看到 WordPress“欢迎”页面。 配置 WordPress 安装并开始使用它！

    ![WordPress 配置 - Azure 应用服务中的首个 WordPress](./media/app-service-web-get-started-php-portal/wordpress-config.png)
    
## <a name="next-steps"></a>后续步骤
* [创建、配置 Laravel Web 应用并将其部署到 Azure](app-service-web-php-get-started.md) - 了解在 Azure 中运行任何 PHP Web 应用所需的基本技能，如：

    * 通过 PowerShell/Bash 在 Azure 中创建并配置应用。
    * 设置 PHP 版本。
    * 使用不在根应用程序目录中的开始文件。
    * 实现 Commposer 自动化。
    * 访问环境特定的变量。
    * 排查常见错误。

* [将代码部署到 Azure 应用服务](web-sites-deploy.md) - 了解如何从 FTP 或从源代码管理存储库进行部署。
* [在第一个 Web 应用中添加功能](app-service-web-get-started-2.md) - 使 Azure 应用上升到更高的层次。 对用户进行身份验证。 按需缩放。 设置一些性能警报。 所有这些操作只需按几下鼠标即可完成。

