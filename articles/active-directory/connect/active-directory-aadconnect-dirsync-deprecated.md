---
title: "从 DirSync 和 Azure AD Sync 升级 | Microsoft Docs"
description: "介绍如何从 DirSync 和 Azure AD Sync 升级到 Azure AD Connect。"
services: active-directory
documentationcenter: 
author: andkjell
manager: femila
editor: 
ms.assetid: bd68fb88-110b-4d76-978a-233e15590803
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/13/2017
ms.author: billmath
ms.custom: H1Hack27Feb2017
ms.translationtype: HT
ms.sourcegitcommit: 19be73fd0aec3a8f03a7cd83c12cfcc060f6e5e7
ms.openlocfilehash: 3674670e10500d2992539ab60fbdb31b666fcf9a
ms.contentlocale: zh-cn
ms.lasthandoff: 07/13/2017

---

# <a name="upgrade-windows-azure-active-directory-sync-and-azure-active-directory-sync"></a>升级 Windows Azure Active Directory Sync 和 Azure Active Directory Sync
Azure AD Connect 是连接本地目录与 Azure AD 和 Office 365 的最佳方式。 这是将 Azure AD Connect 从 Microsoft Azure Active Directory Sync (DirSync) 或 Azure AD Sync 升级的最佳时机，由于这些工具现在已弃用，并在 2017 年 4 月 13 日结束支持。

已弃用的两个标识同步工具提供给单一林客户 (DirSync)，以及多林和其他高级客户 (Azure AD Sync)。 这些较旧的工具已经替换为适用于所有方案的单一解决方案：Azure AD Connect。 它提供新的功能、增强功能和新方案的支持。 若要能够继续同步本地标识数据到 Azure AD 和 Office 365，强烈建议升级到 Azure AD Connect。

最新版 DirSync 已在 2014 年 7 月发布，最新版 Azure AD Sync 已在 2015 年 5 月发布。

## <a name="what-is-azure-ad-connect"></a>什么是 Azure AD Connect
Azure AD Connect 是 DirSync 和 Azure AD Sync 的后继产品。 它结合了两者支持的所有方案。 可以在[将本地标识与 Azure Active Directory 集成](active-directory-aadconnect.md)中了解详细信息。

## <a name="deprecation-schedule"></a>弃用计划
| 日期 | 注释 |
| --- | --- |
| 2016 年 4 月 13 日 |Microsoft Azure Active Directory Sync (DirSync) 和 Azure Active Directory Sync (Azure AD Sync) 已宣布弃用。 |
| 2017 年 4 月 13 日 |结束支持。 客户必须先升级到 Azure AD Connect 才能建立支持案例。 |
|2017 年 12 月 31 日|Azure AD 将不再接受来自 Windows Azure Active Directory 同步（“DirSync”）和 Microsoft Azure Active Directory 同步（“Azure AD Sync”）的通信。

## <a name="how-to-transition-to-azure-ad-connect"></a>如何过渡到 Azure AD Connect
如果你正在运行 DirSync，可通过两种方式升级：就地升级和并行部署。 对大多数客户，如果使用最新的操作系统并且对象数少于 50,000 个，我们建议使用就地升级。 对于其他情况，建议执行并行部署，这样，DirSync 配置将迁移到运行 Azure AD Connect 的新服务器。

如果使用 Azure AD Sync，则建议使用就地升级。 如果需要，也可以并行安装新的 Azure AD Connect 服务器，并运行从 Azure AD 同步服务器到 Azure AD Connect 的交叉迁移。

| 解决方案 | 方案 |
| --- | --- |
| [从 DirSync 升级](active-directory-aadconnect-dirsync-upgrade-get-started.md) |<li>如果有已在运行的现有 DirSync 服务器。</li> |
| [从 Azure AD Sync 升级](active-directory-aadconnect-upgrade-previous-version.md) |<li>如果要从 Azure AD Sync 迁移。</li> |

如果想要了解如何从 DirSync 就地升级到 Azure AD Connect，请观看第 9 频道视频：

> [!VIDEO https://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-in-place-upgrade-from-legacy-tools/player]
>
>

## <a name="faq"></a>常见问题
**问：我收到了 Azure 团队发来的电子邮件通知和/或 Office 365 消息中心发来的消息，但我使用的是 Connect。**  
该通知还会发送到使用内部版本为 1.0.\*.0 的 Azure AD Connect 的客户（使用 1.1 以前的版本）。 Microsoft 建议客户使用最新的 Azure AD Connect 版本。 在版本 1.1 中引入的[自动升级](active-directory-aadconnect-feature-automatic-upgrade.md)功能始终可让客户轻松安装最新版本的 Azure AD Connect。

**问：DirSync/Azure AD Sync 将在 2017 年 4 月 13 日停用吗？**  
DirSync/Azure AD Sync 将在 2017 年 4 月 13 日继续工作。  但从 2017 年 12 月 31 日起，Azure AD 将不再接受来自 DirSync/Azure AD Sync 的通信。

**问：可从哪些 DirSync 版本升级？**  
支持从当前所用的任何 DirSync 版本升级。

**问：用于 FIM/MIM 的 Azure AD 连接器的情况怎样？**  
用于 FIM/MIM 的 Azure AD 连接器**尚未**宣布弃用。 它目前处于**功能冻结**状态；其中不会添加任何功能，也不会接受任何 bug 修复。 Microsoft 建议其用户计划好迁移到 Azure AD Connect。 我们强烈建议不要使用它来启动任何新部署。 今后我们将宣布弃用此连接器。

## <a name="additional-resources"></a>其他资源
* [将本地标识与 Azure Active Directory 集成](active-directory-aadconnect.md)

