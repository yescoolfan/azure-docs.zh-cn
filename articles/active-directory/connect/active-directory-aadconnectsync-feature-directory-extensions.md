---
title: "Azure AD Connect 同步：目录扩展 | Microsoft Docs"
description: "本主题介绍 Azure AD Connect 中的目录扩展功能。"
services: active-directory
documentationcenter: 
author: AndKjell
manager: femila
editor: 
ms.assetid: 995ee876-4415-4bb0-a258-cca3cbb02193
ms.service: active-directory
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 07/12/2017
ms.author: billmath
ms.translationtype: Human Translation
ms.sourcegitcommit: 2f5c5e9af193c843765f63640d46c25f3a6d10c3
ms.openlocfilehash: 3641f9309cc38f6575ce36d3450448cdae1601a9
ms.contentlocale: zh-cn
ms.lasthandoff: 02/02/2017

---
<a id="azure-ad-connect-sync-directory-extensions" class="xliff"></a>

# Azure AD Connect 同步：目录扩展
目录扩展可让你使用本地 Active Directory 中自己的属性扩展 Azure AD 中的架构。 此功能可以构建 LOB 应用来使用要在本地持续管理的属性。 可以通过 [Azure AD Graph 目录扩展](https://msdn.microsoft.com/Library/Azure/Ad/Graph/howto/azure-ad-graph-api-directory-schema-extensions)或 [Microsoft Graph](https://graph.microsoft.io/) 使用这些属性。 使用 [Azure AD Graph 资源管理器](https://graphexplorer.cloudapp.net)和 [Microsoft Graph 资源管理器](https://graphexplorer2.azurewebsites.net/)分别可以查看可用属性。

目前没有任何 Office 365 工作负荷使用这些属性。

在安装向导的自定义设置路径中配置要同步的其他属性。
![架构扩展向导](./media/active-directory-aadconnectsync-feature-directory-extensions/extension2.png)  
安装显示以下属性，它们是有效的候选项：

* “用户”和“组”对象类型
* 单值属性：String、Boolean、Integer、Binary
* 多值属性：String、Binary

属性列表是在安装 Azure AD Connect 过程中从架构缓存读取的。 如果已使用附加属性扩展 Active Directory 架构，则只有在[刷新架构](active-directory-aadconnectsync-installation-wizard.md#refresh-directory-schema)后，这些新属性才可见。

Azure AD 中的对象最多可以有 100 个目录扩展属性。 最大长度为 250 个字符。 如果属性值更长，则将被同步引擎截断。

在安装 Azure AD Connect 期间，将会注册可以使用这些属性的应用程序。 可以在 Azure 门户中看到此应用程序。  
![架构扩展应用](./media/active-directory-aadconnectsync-feature-directory-extensions/extension3new.png)

现在可以通过 Graph 使用这些属性：  
![图形](./media/active-directory-aadconnectsync-feature-directory-extensions/extension4.png)

这些属性的前面带有 extension\_{AppClientId}\_ 前缀。 Azure AD 租户中的所有属性具有相同的 AppClientId 值。

<a id="next-steps" class="xliff"></a>

## 后续步骤
了解有关 [Azure AD Connect 同步](active-directory-aadconnectsync-whatis.md)配置的详细信息。

了解有关 [将本地标识与 Azure Active Directory 集成](active-directory-aadconnect.md)的详细信息。

