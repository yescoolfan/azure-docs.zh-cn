---
title: "Azure AD Synchronization Service Manager UI 中的连接器 | Microsoft 文档"
description: "了解 Azure AD Connect 的 Synchronization Service Manager 中的“连接器”选项卡。"
services: active-directory
documentationcenter: 
author: andkjell
manager: femila
editor: 
ms.assetid: 60f1d979-8e6d-4460-aaab-747fffedfc1e
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/13/2017
ms.author: billmath
ms.custom: H1Hack27Feb2017
ms.translationtype: Human Translation
ms.sourcegitcommit: eeb56316b337c90cc83455be11917674eba898a3
ms.openlocfilehash: 6d893efd775ff6b55524ba3a621d8248adbdd432
ms.contentlocale: zh-cn
ms.lasthandoff: 04/03/2017

---
# 将连接器与 Azure AD Connect Sync Service Manager 配合使用
<a id="using-connectors-with-the-azure-ad-connect-sync-service-manager" class="xliff"></a>

![Sync Service Manager](./media/active-directory-aadconnectsync-service-manager-ui/connectors.png)

“连接器”选项卡可用于管理同步引擎连接的所有系统。

## 连接器操作
<a id="connector-actions" class="xliff"></a>
| 操作 | 注释 |
| --- | --- |
| 创建 |请勿使用。 若要连接到其他 AD 林，请使用安装向导。 |
| 属性 |用于域和 OU 筛选。 |
| [删除](#delete) |用于删除连接器空间中的数据或删除与林的连接。 |
| [配置运行配置文件](#configure-run-profiles) |除了域筛选，不会在此处进行任何配置。 可以通过此操作来查看已配置的运行配置文件。 |
| 运行 |用于启动配置文件的一次性运行。 |
| 停止 |停止当前运行配置文件的连接器。 |
| 导出连接器 |请勿使用。 |
| 导入连接器 |请勿使用。 |
| 更新连接器 |请勿使用。 |
| 刷新架构 |刷新缓存架构。 最好改在安装向导中使用此选项，因为它也会更新同步规则。 |
| [搜索连接器空间](#search-connector-space) |用于查找对象，以及[在整个系统中跟踪对象及其数据](#follow-an-object-and-its-data-through-the-system)。 |

### 删除
<a id="delete" class="xliff"></a>
删除操作适用于两种不同的用途。  
![Sync Service Manager](./media/active-directory-aadconnectsync-service-manager-ui/connectordelete.png)

“仅删除连接器空间”选项会删除所有数据，但保留所有配置。

“删除连接器和连接器空间”选项会删除数据以及所有配置。 不想再连接到林时可以使用此选项。

这两个选项都会同步所有对象，并更新 Metaverse 对象。 这是一个长时间运行的操作。

### 配置运行配置文件
<a id="configure-run-profiles" class="xliff"></a>
此选项可让你查看为连接器配置的运行配置文件。

![Sync Service Manager](./media/active-directory-aadconnectsync-service-manager-ui/configurerunprofiles.png)

### 搜索连接器空间
<a id="search-connector-space" class="xliff"></a>
查找对象和排查数据问题时，搜索连接器空间操作非常有用。

![Sync Service Manager](./media/active-directory-aadconnectsync-service-manager-ui/cssearch.png)

先选择一个“范围”。 你可以基于数据（RDN、DN、定位点、子树）或对象状态（所有其他选项）进行搜索。  
![Sync Service Manager](./media/active-directory-aadconnectsync-service-manager-ui/cssearchscope.png)  
例如，如果进行子树搜索，将获取某个 OU 中的所有对象。  
![Sync Service Manager](./media/active-directory-aadconnectsync-service-manager-ui/cssearchsubtree.png)  
可以从此网格中选择一个对象，选择“属性”，并从源连接器空间到 Metaverse 再到目标连接器空间一直[跟踪对象](active-directory-aadconnectsync-troubleshoot-object-not-syncing.md)。

### 更改 AD DS 帐户密码
<a id="changing-the-ad-ds-account-password" class="xliff"></a>
如果更改帐户密码，Synchronization Service 将不再能将更改导入/导出到本地 AD。   可能会看到如下内容：

- AD 连接器的导入/导出步骤失败，错误为“no-start-credentials”。
- 在 Windows 事件查看器下，应用程序事件日志包含一个错误，事件 ID 为 6000，消息为“管理代理‘contoso.com’未能运行，因为凭据无效”。

若要解决此问题，请使用以下方法更新 AD DS 用户帐户：


1. 启动 Synchronization Service Manager（“开始”→ Synchronization Service）。
</br>![Sync Service Manager](./media/active-directory-aadconnectsync-service-manager-ui/startmenu.png)
2. 转到“连接器”选项卡。
3. 选择配置为使用 AD DS 帐户的 AD 连接器。
4. 在“操作”下，选择“属性”。
5. 在弹出对话框中，选择“连接到 Active Directory 林”：
6. 林名称指示相应的本地 AD。
7. 用户名指示用于同步的 AD DS 帐户。
8. 在密码文本框 ![Azure AD Connect 同步加密密钥实用程序](media/active-directory-aadconnectsync-encryption-key/key6.png)中输入 AD DS 帐户的新密码
9. 单击“确定”以保存新密码，并重启 Synchronization Service 以从内存缓存中删除旧密码。



## 后续步骤
<a id="next-steps" class="xliff"></a>
了解有关 [Azure AD Connect 同步](active-directory-aadconnectsync-whatis.md)配置的详细信息。

了解有关 [将本地标识与 Azure Active Directory 集成](active-directory-aadconnect.md)的详细信息。

