---
title: "Azure Active Directory 中的管理单元管理"
description: "在 Azure Active Directory 中使用管理单元获得更精细的委派权限"
services: active-directory
documentationcenter: 
author: curtand
manager: femila
editor: 
ms.assetid: 8464cd6b-1d1a-470d-a4fb-ee29b8eab4c4
ms.service: active-directory
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 05/04/2017
ms.author: curtand
ms.translationtype: Human Translation
ms.sourcegitcommit: 07584294e4ae592a026c0d5890686eaf0b99431f
ms.openlocfilehash: 355ae7a13ab3d32b69a2b90e5410d5fc90fb6916
ms.contentlocale: zh-cn
ms.lasthandoff: 06/02/2017


---
# <a name="administrative-units-management-in-azure-ad---public-preview"></a>Azure AD - 公共预览版中的管理单元管理
本文介绍管理单元，这是一个新的 Azure Active Directory 资源容器，可用于向部分用户委托管理权限，以及向部分用户应用策略。 在 Azure Active Directory 中，利用管理单元，中心管理员能够将权限委派给区域管理员或以粒度级别设置策略。

这在具有独立部门的组织中非常有用，例如：由互相独立的许多自治学校（商学院和工程学校等）组成的大型大学。 此类部门具有其自己的 IT 管理员，这些管理员会控制访问、管理用户并专门针对其部门设置策略。 中心管理员希望能够通过其特定部门中的用户授予这些部门管理员权限。 更具体地说，通过使用此示例，例如，中心管理员可以创建特定学校（商学院）的管理单元并仅使用商学院用户填充该单元。 然后，中心管理员可以将商学院的 IT 员工添加到限定范围的角色中，换而言之，只通过商学院管理单元为 IT 员工授予商学院管理权限。

> [!IMPORTANT]
> 只能在启用 Azure Active Directory Premium 的情况下分配管理单元范围的管理员角色。 有关详细信息，请参阅 [Azure AD Premium 入门](active-directory-get-started-premium.md)。
>


从中央管理员的角度来看，管理单元是可以创建并填充资源的目录对象。 **在此预览版中，这些资源只能是用户。** 一旦创建并填充，管理单元即可作为只通过管理单元中所含资源限制授予的权限的范围。

## <a name="managing-administrative-units"></a>管理管理单元
在此预览版中，你可以使用 Windows PowerShell cmdlet 的 Azure Active Directory 模块创建和管理管理单元。 若要深入了解如何执行此操作，请参阅[使用管理单元](https://docs.microsoft.com/en-us/powershell/azure/working-with-administrative-units?view=azureadps-2.0)

有关软件要求和安装 Azure AD 模块的详细信息，以及有关用于管理管理单元的 Azure AD 模块 cmdlet 的信息（包括语法、参数说明和示例），请参阅[使用 Windows PowerShell 管理 Azure AD](https://msdn.microsoft.com/library/azure/jj151815.aspx)。

## <a name="next-steps"></a>后续步骤
[Azure Active Directory 版本](active-directory-editions.md)

