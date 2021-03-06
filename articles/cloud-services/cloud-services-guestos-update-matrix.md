---
title: "了解最新的 Azure 来宾 OS 版本 | Microsoft Docs"
description: "有关 Azure 云服务来宾 OS 的最新发行新闻以及 SDK 兼容性。"
services: cloud-services
documentationcenter: na
author: raiye
manager: timlt
editor: 
ms.assetid: 6306cafe-1153-44c7-8554-623b03d59a34
ms.service: cloud-services
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: tbd
ms.date: 8/3/2017
ms.author: raiye
ms.translationtype: HT
ms.sourcegitcommit: 8b857b4a629618d84f66da28d46f79c2b74171df
ms.openlocfilehash: acb22517cb1ce3fe166ae149d4d5bfb867b5ab99
ms.contentlocale: zh-cn
ms.lasthandoff: 08/04/2017

---
# <a name="azure-guest-os-releases-and-sdk-compatibility-matrix"></a>Azure 来宾 OS 版本和 SDK 兼容性对照表
提供适用于云服务的最新 Azure 来宾 OS 版本的最新信息。 此信息可帮助在禁用来宾 OS 之前规划升级路径。 如果根据 [Azure 来宾 OS 更新设置][Azure Guest OS Update Settings]中所述将角色配置为使用自动进行来宾 OS 更新，则不一定要阅读本页面。

> [!IMPORTANT]
> 本页面适用于在来宾 OS 顶层运行的云服务 Web 角色和辅助角色， 而**不适用于** IaaS 虚拟机。
>
>


> [!NOTE]
> 最近已弃用 RSS 源。 请留意即将推出的新源更新！
>
>

不太确定什么是来宾 OS 或者来宾 OS 的工作原理？ 请阅读[此部分](#how-it-works)。

## <a name="news-updates"></a>新闻更新

###### <a name="august-3-2017"></a>**2017 年 8 月 3 日**
6 月版来宾 OS 已发布。

###### <a name="july-19-2017"></a>**2017 年 7 月 19 日**
7 月版来宾 OS 将从 7 月 19 日开始推出，预计于 8 月 8 日正式发行。

###### <a name="july-7-2017"></a>**2017 年 7 月7 日**
6 月版来宾 OS 已发布。

###### <a name="june-16-2017"></a>**2017 年 6 月 16 日**
6 月版来宾 OS 将从 6 月 16 日开始推出，预计于 7 月 11 日正式发行。

###### <a name="june-5-2017"></a>**2017 年 6 月 5 日**
5 月版来宾 OS 已发布。

###### <a name="may-17-2017"></a>**2017 年 5 月 17 日**
由于存在安全 bug，我们将禁用以下 2016 年 12 月和 2017 年 1 月的 OS 版本，这些版本不包含门户的[修补程序]：WA-GUEST-OS-5.4_201612-01、WA-GUEST-OS-4.39_201612-01、WA-GUEST-OS-3.46_201612-01、WA-GUEST-OS-2.59_201701-01

###### <a name="may-12-2017"></a>**2017 年 5 月 12 日**
5 月版来宾 OS 将从 5 月 12 日开始推出，预计于 6 月 13 日正式发行。

###### <a name="april-18-2017"></a>**2017 年 4 月 18 日**
4 月版来宾 OS 将从 4 月 18 日开始推出，预计于 5 月 9 日正式发行。

###### <a name="april-10-2017"></a>**2017 年 4 月 10 日**
3 月版来宾 OS 已于 2017 年 3 月 14 日开始推出，已于 2017 年 4 月 10 日发行。

###### <a name="january-10-2017"></a>**2017 年 1 月 10 日**
1 月来宾 OS 包含仅影响 OS 系列 2 (Windows 2008 Server R2) 的修补程序。 因此，本月仅发布了 OS 系列 2 映像 (WA-GUEST-OS-2.59_201701-01)。 对于所有其他 OS 系列，12 月版 OS (201612-01) 仍为最新版。


## <a name="releases"></a>发行版本
## <a name="family-5-releases"></a>系列 5 发行版本
**Windows Server 2016**

安装的 .NET Framework：4.0、4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2

> [!NOTE]
> 标有 * 的日期可随时更改。
>
> OS 系列 5 的 RDP 密码至少必须有 10 个字符。
>

| 配置字符串 | 发行日期 | 停用日期 | 失效日期 |
| --- | --- | --- | --- |
| WA-GUEST-OS-5.9_201707-01 |2017 年 8 月 3 日 |5.11 版发行后 |TBD |
| WA-GUEST-OS-5.8_201706-01 |2017 年 7 月 7日 |5.10 版发行后 |TBD |
| WA-GUEST-OS-5.7_201705-01 |2017 年 6 月 5日 |5.9 版发行后 |TBD |
|~~WA-GUEST-OS-5.6_201704-01~~ |2017 年 5 月 9 日 |2017 年 8 月 3 日 |TBD |
|~~WA-GUEST-OS-5.5_201703-01~~ |2017 年 4 月 10 日 |2017 年 7 月 7日 |TBD |
|~~WA-GUEST-OS-5.4_201612-01~~ |2017 年 1 月 10 日 |2017 年 6 月 5日|TBD |
|~~WA-GUEST-OS-5.3_201611-01~~ |2016 年 12 月 14 日 |2017 年 5 月 9 日 |TBD |
|~~WA-GUEST-OS-5.2_201610-02~~ |2016 年 11 月 1 日 |2017 年 4 月 10 日 |TBD |

## <a name="family-4-releases"></a>系列 4 发行版本
**Windows Server 2012 R2**

支持 .NET 4.0、4.5、4.5.1、4.5.2

> [!NOTE]
> 标有 * 的日期可随时更改
>
>

| 配置字符串 | 发行日期 | 停用日期 | 失效日期 |
| --- | --- | --- | --- |
| WA-GUEST-OS-4.44_201707-01 |2017 年 8 月 3 日 |4.46 版发行后 |TBD |
| WA-GUEST-OS-4.43_201706-01 |2017 年 7 月 7日 |4.45 版发行后 |TBD |
| WA-GUEST-OS-4.42_201705-01 |2017 年 6 月 5日 |4.44 版发行后 |TBD |
|~~WA-GUEST-OS-4.41_201704-01~~ |2017 年 5 月 9 日 |2017 年 8 月 3 日 |TBD |
|~~WA-GUEST-OS-4.40_201703-01~~ |2017 年 4 月 10 日 |2017 年 7 月 7日 |TBD |
|~~WA-GUEST-OS-4.39_201612-01~~ |2017 年 1 月 10 日 |2017 年 6 月 5日 |TBD |
|~~WA-GUEST-OS-4.38_201611-01~~ |2016 年 12 月 14 日 |2017 年 5 月 9 日 |TBD |
|~~WA-GUEST-OS-4.37_201610-02~~ |2016 年 11 月 16 日 |2017 年 4 月 10 日 |TBD |
|~~WA-GUEST-OS-4.36_201609-01~~ |2016 年 10 月 13 日 |2017 年 1 月 14 日 |TBD |
|~~WA-GUEST-OS-4.35_201608-01~~ |2016 年 9 月 13 日 |2016 年 12 月 16 日 |TBD |
|~~WA-GUEST-OS-4.34_201607-01~~ |2016 年 8 月 8 日 |2016 年 11 月 13 日 |TBD |


## <a name="family-3-releases"></a>系列 3 发行版本
**Windows Server 2012**

支持 .NET 4.0、4.5、4.5.1、4.5.2

> [!NOTE]
> 标有 * 的日期可随时更改
>
>

| 配置字符串 | 发行日期 | 停用日期 | 失效日期 |
| --- | --- | --- | --- |
| WA-GUEST-OS-3.51_201707-01 |2017 年 8 月 3 日 |3.53 版发行后 |TBD |
| WA-GUEST-OS-3.50_201706-01 |2017 年 7 月 7日 |3.52 版发行后 |TBD |
| WA-GUEST-OS-3.49_201705-01 |2017 年 6 月 5日 |3.51 版发行后 |TBD |
|~~WA-GUEST-OS-3.48_201704-01~~ |2017 年 5 月 9 日 |2017 年 8 月 3 日 |TBD |
|~~WA-GUEST-OS-3.47_201703-01~~ |2017 年 4 月 10 日 |2017 年 7 月 7日 |TBD |
|~~WA-GUEST-OS-3.46_201612-01~~ |2017 年 1 月 10 日 |2017 年 6 月 5日 |TBD |
|~~WA-GUEST-OS-3.45_201611-01~~ |2016 年 12 月 14 日 |2017 年 5 月 9 日 |TBD |
|~~WA-GUEST-OS-3.44_201610-02~~ |2016 年 11 月 16 日 |2017 年 5 月 1 日 |TBD |
|~~WA-GUEST-OS-3.43_201609-01~~ |2016 年 10 月 13 日 |2017 年 1 月 14 日 |TBD |
|~~WA-GUEST-OS-3.42_201608-01~~ |2016 年 9 月 13 日 |2016 年 12 月 16 日 |TBD |
|~~WA-GUEST-OS-3.41_201607-01~~ |2016 年 8 月 8 日 |2016 年 11 月 13 日 |TBD |


## <a name="family-2-releases"></a>系列 2 发行版本
**Windows Server 2008 R2 SP1**

支持 .NET 3.5、4.0、4.5、4.5.1、4.5.2

> [!NOTE]
> 标有 * 的日期可随时更改
>
>

| 配置字符串 | 发行日期 | 停用日期 | 失效日期 |
| --- | --- | --- | --- |
| WA-GUEST-OS-2.64_201707-01 |2017 年 8 月 3 日 |2.66 版发行后 |TBD |
| WA-GUEST-OS-2.63_201706-01 |2017 年 7 月 7日 |2.65 版发行后 |TBD |
| WA-GUEST-OS-2.62_201705-01 |2017 年 6 月 5日 |2.64 版发行后 |TBD |
|~~WA-GUEST-OS-2.61_201704-01~~ |2017 年 5 月 9 日 |2017 年 8 月 3 日 |TBD |
|~~WA-GUEST-OS-2.60_201703-01~~ |2017 年 4 月 10 日 |2017 年 7 月 7日 |TBD |
|~~WA-GUEST-OS-2.59_201701-01~~ |2017 年 1 月 10 日 |2017 年 6 月 5日 |TBD |
|~~WA-GUEST-OS-2.58_201612-01~~ |2017 年 1 月 10 日 |2017 年 5 月 9 日|TBD |
|~~WA-GUEST-OS-2.57_201611-01~~ |2016 年 12 月 14 日 |2017 年 4 月 10 日 |TBD |
|~~WA-GUEST-OS-2.56_201610-02~~ |2016 年 11 月 16 日 |2017 年 2 月 10 日 |TBD |
|~~WA-GUEST-OS-2.55_201609-01~~ |2016 年 10 月 13 日 |2017 年 1 月 14 日 |TBD |
|~~WA-GUEST-OS-2.54_201608-01~~ |2016 年 9 月 13 日 |2016 年 12 月 16 日 |TBD |
|~~WA-GUEST-OS-2.53_201607-01~~ |2016 年 8 月 8 日 |2016 年 11 月 13 日 |TBD |



## <a name="msrc-patch-updates"></a>MSRC 修补程序更新
[此处][patches]提供了每月来宾 OS 版本随附的修补程序列表。

## <a name="sdk-support"></a>SDK 支持
尽管 [Azure SDK 停用策略][retire policy sdk]指出仅支持 2.2 以上的版本，但特定的来宾 OS 允许使用早期版本。 你应该始终使用最新的受支持 SDK。

| 来宾 OS 系列 | 兼容的 SDK 版本 |
| --- | --- |
| 5 |版本 2.9.5.1+ |
| 4 |版本 2.1+ |
| 3 |版本 1.8+ |
| 2 |版本 1.3+ |
| 1 |版本 1.0+ |

## <a name="guest-os-release-information"></a>来宾 OS 版本信息
来宾 OS 发行版有三个重要的日期：**发行日期**、**停用日期**和**失效日期**。 来宾 OS 在门户中可用，并可选作目标来宾 OS。 当来宾 OS 到达停用日期时，将从 Azure 中删除。 但是，面向该来宾 OS 的任何云服务仍会正常运行。

在停用日期与失效日期之间有一个缓冲期，可让你轻松地从一个来宾 OS 版本转换到新的版本。 如果正在使用*自动更新版*的来宾 OS，则始终可以获得最新版本，而无需担心失效的问题。

**到期**日期过后，仍旧使用该来宾 OS 的所有云服务将被停止、删除或强行升级。 可在[此处][retirepolicy]了解有关停用策略的详细信息。

## <a name="guest-os-family-version-explanation"></a>来宾 OS 系列版本解释
来宾 OS 系列基于发布的 Microsoft Windows Server 版本。 来宾 OS 是运行 Azure 云服务的基本操作系统。 每个来宾 OS 都具有系列、版本和版本号。

* **来宾 OS 系列**  
  来宾 OS 所基于的 Windows Server 操作系统版本。 例如，*系列 3* 基于 Windows Server 2012。
* **来宾 OS 版本**  
  来宾 OS 系列映像和在生成新的来宾 OS 版本时提供的相关 [Microsoft 安全响应中心 (MSRC)][msrc] 修补程序。 并非提供了所有修补程序。

    版本号从 0 开始，并在每次添加新的一组更新时增加 1。 仅在比较重要时，才会显示尾随零。 即，2.10 版是与 2.1 版不同的版本，并且比它晚得多。
* **来宾 OS 发行版**  
  来宾 OS 版本的再发行版。 如果 Microsoft 在测试期间发现需要更改的问题，就会出现再发行版。 最新的发行版始终会取代任何以前的发行版（无论是否公开）。 Azure 门户将只允许用户选取给定版本的最新发行版。 通常，不会对运行在以前版本上的部署进行强制升级，具体取决于 Bug 的严重性。

在下面的示例中，2 是系列，12 是版本，而“rel2”是发行版本。

**来宾 OS 发行版** - 2.12 rel2

**此发行版本的配置字符串** - WA-GUEST-OS-2.12_201208-02

来宾 OS 的配置字符串嵌入了该相同信息，以及显示考虑为该发行版本包括哪些 MSRC 修补程序的日期。 在此示例中，考虑包括 2012 年 8 月之前（含该日期）为 Windows Server 2008 R2 开发的 MSRC 修补程序。 仅包括专门应用于该版本的 Windows Server 的修补程序。 例如，如果某个 MSRC 修补程序应用于 Microsoft Office，则它将不包括在内，因为该产品不属于 Windows Server 基本映像。

## <a name="guest-os-system-update-process"></a>来宾 OS 系统更新过程
本页包含有关即将发布的来宾 OS 版本的信息。 客户已表明想知道什么时候发行版本，因为如果未设为“自动”更新，他们的云服务角色将重新启动。 来宾 OS 发行版通常会在每月第二个星期二发布 MSRC 更新之后的至少五 (5) 天发布。 新版本包含针对每个来宾 OS 系列的所有相关 MSRC 修补程序。

Microsoft Azure 不断地发布更新。 来宾 OS 只不过是此类更新的其中一种。 一个发行版本会受到许多因素影响，不胜列举。 此外，Azure 实际上在成千上万的计算机上运行。 这意味着无法提供重新启动你角色的准确日期和时间。 我们正在制定限制或定时重新启动的计划。

在发布新的来宾 OS 发行版本时，可能需要一段时间才能在 Azure 中完全传播。 在将服务更新为新的来宾 OS 时，将重新启动这些服务以满足更新域限制。 设置为使用“自动”更新的服务将先获取发行版本。 更新后将在 Azure 门户中显示为所选服务列出的新来宾 OS 版本。 在此期间，可能会发布再发行版本。 某些版本可能需要较长的部署时间，可能不会在正式发行日期后的几个星期内执行自动升级重新启动。 在来宾 OS 可用后，你可以从门户或配置文件中显式选择该版本。

有关重启和指针的大量宝贵信息以及有关来宾和主机操作系统更新的更多技术详情，请阅读 MSDN 博客文章[角色实例因操作系统升级而重新启动][restarts]。

如果手动更新来宾 OS，请参阅[来宾 OS 停用策略][retirepolicy]获取其他信息。

## <a name="guest-os-supportability-and-retirement-policy"></a>来宾 OS 可支持性和停用策略
[此处][retirepolicy]解释了来宾 OS 可支持性和停用策略。

[Install .NET on a Cloud Service Role]: https://azure.microsoft.com/en-us/documentation/articles/cloud-services-dotnet-install-dotnet/?WT.mc_id=azurebg_email_Trans_963_RevisedNET_Update
[Azure Guest OS Update Settings]: cloud-services-how-to-configure.md
[ssl3 announcement]: http://azure.microsoft.com/blog/2014/12/09/azure-security-ssl-3-0-update/
[Microsoft Security Advisory 3009008]: https://technet.microsoft.com/library/security/3009008.aspx
[ssl3-fixit]: http://go.microsoft.com/?linkid=9863266
[MS14-066]: https://technet.microsoft.com/library/security/ms14-066.aspx
[MS14-046]: https://technet.microsoft.com/library/security/ms14-046.aspx
[retire policy sdk]: https://msdn.microsoft.com/library/dn479282.aspx
[server and gos]: https://msdn.microsoft.com/library/dn775043.aspx
[azuresupport]: http://azure.microsoft.com/support/options/
[net install pkg]: http://www.microsoft.com/download/details.aspx?id=42643
[msrc]: http://www.microsoft.com/security/msrc/default.aspx
[update guest os portal]: https://msdn.microsoft.com/library/gg433101.aspx
[update guest os svc]: https://msdn.microsoft.com/library/gg456324.aspx
[restarts]: http://blogs.msdn.com/b/kwill/archive/2012/09/19/role-instance-restarts-due-to-os-upgrades.aspx
[patches]: cloud-services-guestos-msrc-releases.md
[retirepolicy]: cloud-services-guestos-retirement-policy.md
[fam1retire]: cloud-services-guestos-family1-retirement.md
[修补程序]: https://technet.microsoft.com/en-us/library/security/ms17-010.aspx

