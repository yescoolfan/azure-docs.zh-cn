---
title: "教程：Azure Active Directory 与 StatusPage 集成 | Microsoft 文档"
description: "了解如何在 Azure Active Directory 和 StatusPage 之间配置单一登录。"
services: active-directory
documentationcenter: 
author: jeevansd
manager: femila
editor: 
ms.assetid: f6ee8bb3-df43-4c0d-bf84-89f18deac4b9
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/13/2017
ms.author: jeedes
translationtype: Human Translation
ms.sourcegitcommit: 7cc133d6289bffbc3b7fc591104bc51ebfc67ddd
ms.openlocfilehash: 3b901bcb08a194f72c3dc75e33f2b94fffea370e
ms.lasthandoff: 02/17/2017


---
# <a name="tutorial-azure-active-directory-integration-with-statuspage"></a>教程：Azure Active Directory 与 StatusPage 集成
本教程的目的是说明如何将 StatusPage 与 Azure Active Directory (Azure AD) 集成。

将 StatusPage 与 Azure AD 集成提供以下优势： 

* 可在 Azure AD 中控制谁有权访问 StatusPage 
* 可以让用户使用其 Azure AD 帐户自动登录到 StatusPage 单一登录 (SSO)
* 可以在一个中心位置（即 Azure 经典门户）管理帐户

如果要了解有关 SaaS 应用与 Azure AD 集成的更多详细信息，请参阅 [Azure Active Directory 的应用程序访问与单一登录是什么](active-directory-appssoaccess-whatis.md)。

## <a name="prerequisites"></a>先决条件
若要配置 Azure AD 与 StatusPage 的集成，需备齐以下项目：

* Azure AD 订阅
* 已启用 StatusPage 单一登录 (SSO) 的订阅

>[!NOTE]
>不建议使用生产环境测试本教程中的步骤。 
> 

测试本教程中的步骤应遵循以下建议：

* 不应使用生产环境，除非有此必要。
* 如果没有 Azure AD 试用环境，可以获取[一个月的试用版](https://azure.microsoft.com/pricing/free-trial/)。 

## <a name="scenario-description"></a>方案描述
本教程旨在介绍如何在测试环境中测试 Azure AD SSO。 

本教程中概述的方案包括两个主要构建基块：

* 从库中添加 StatusPage 
* 配置和测试 Azure AD SSO

## <a name="add-statuspage-from-the-gallery"></a>从库添加 StatusPage
若要配置 StatusPage 与 Azure AD 的集成，需要从库中将 StatusPage 添加到托管 SaaS 应用列表。

**若要从库中添加 StatusPage，请执行以下步骤：**

1. 在 **Azure 经典门户**中，在左侧导航窗格上，单击“Active Directory”。 
   
    ![Active Directory][1]
2. 从“目录”列表中，选择要为其启用目录集成的目录。
3. 若要打开应用程序视图，请在目录视图的顶部菜单中，单击“应用程序”。
   
    ![应用程序][2]
4. 在页面底部单击“添加”。
   
    ![应用程序][3]
5. 在“要执行什么操作”对话框中，单击“从库中添加应用程序”。
   
    ![应用程序][4]
6. 在搜索框中，键入“StatusPage”。
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_01.png)
7. 在结果窗格中，选择“StatusPage”，然后单击“完成”以添加该应用程序。
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_02.png)

## <a name="configure-and-test-azure-ad-sso"></a>配置和测试 Azure AD SSO
本部分的目的是说明如何基于名为“Britta Simon”的测试用户配置和测试 StatusPage 的 Azure AD SSO。

若要运行 SSO，Azure AD 需要知道与 Azure AD 用户相对应的 StatusPage 用户。 换句话说，需要在 Azure AD 用户与 StatusPage 中相关用户之间建立链接关系。

通过将 Azure AD 中“用户名”的值分配为 StatusPage 中“用户名”的值来建立此链接关系。

若要配置和测试 StatusPage 的 Azure AD 单一登录，需要完成以下构建基块：

1. **[配置 Azure AD 单一登录](#configuring-azure-ad-single-single-sign-on)** - 让用户能够使用此功能。
2. **[创建 Azure AD 测试用户](#creating-an-azure-ad-test-user)** - 使用 Britta Simon 测试 Azure AD 单一登录。
3. **[创建 StatusPage 测试用户](#creating-a-statuspage-test-user)** - 在 StatusPage 中创建 Britta Simon 的对应用户，将其链接到她的 Azure AD 表示形式。
4. **[分配 Azure AD 测试用户](#assigning-the-azure-ad-test-user)** - 让 Britta Simon 使用 Azure AD 单一登录。
5. **[测试单一登录](#testing-single-sign-on)** - 验证配置是否正常工作。

### <a name="configure-azure-ad-single-sign-on"></a>配置 Azure AD 单一登录
本部分的目的是在 Azure 经典门户中启用 Azure AD SSO并在 StatusPage 应用程序中配置单一登录。 

**若要配置 StatusPage 的 Azure AD SSO，请执行以下步骤：**

1. 在 Azure 经典门户的“StatusPage”应用程序集成页上，单击“配置单一登录”，打开“配置单一登录”对话框。
   
    ![配置单一登录][6] 
2. 在“你希望用户如何登录 StatusPage”页上，选择“Azure AD 单一登录”，然后单击“下一步”。
   
    ![配置单一登录](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_03.png) 
3. 在“配置应用设置”对话框页上，执行以下步骤：
   
    ![配置单一登录](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_04.png) 
   
   >[!NOTE]
   >通过 [SupportTeam@statuspage.io](mailto:SupportTeam@statuspage.io) 联系 StatusPage 支持团队，请求配置单一登录所需的元数据。 
   > 
  1. 从元数据复制“颁发者”值，然后将其粘贴到“标识符”文本框中。
  2. 从元数据复制回复 URL，然后将其粘贴到“回复 URL”文本框中。
  3. 单击“资源组名称” 的 Azure 数据工厂。

4. 在“配置 StatusPage 的单一登录”页上，执行以下步骤：
   
    ![配置单一登录](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_05.png)   
  1. 单击“下载证书”，然后将文件保存在计算机上。
  2. 单击“下一步”。
5. 在另一浏览器窗口中，以管理员身份登录 StatusPage 公司站点。
6. 在主工具栏中，单击“管理帐户”。
   
    ![配置单一登录](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_06.png) 
7. 单击“单一登录”选项卡。 
   
    ![配置单一登录](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_07.png) 
8. 在“SSO 设置”页上，执行以下步骤：
   
    ![配置单一登录](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_08.png)  
  1. 在 Azure 经典门户的“配置 StatusPage 的单一登录”对话框页上，复制“单一登录服务 URL”值，然后将其粘贴到“SSO 目标 URL”文本框中。 
  2. 在记事本中打开下载的证书，复制其内容，然后将其粘贴到“证书”文本框中。 
  3. 单击“保存” 。
9. 在 Azure 经典门户中，选择“单一登录配置确认”，然后单击“下一步”。 
   
    ![Azure AD 单一登录][10]
10. 在“单一登录确认”页上，单击“完成”。  
   
    ![Azure AD 单一登录][11]

### <a name="create-an-azure-ad-test-user"></a>创建 Azure AD 测试用户
本部分的目的是在 Azure 经典门户中创建名为 Britta Simon 的测试用户。

![创建 Azure AD 用户][20]

**若要在 Azure AD 中创建测试用户，请执行以下步骤：**

1. 在 **Azure 经典门户**中，在左侧导航窗格上，单击“Active Directory”。
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/create_aaduser_09.png)  
2. 在“目录”列表中，选择要启用目录集成的目录。
3. 若要显示用户列表，请在顶部菜单中，单击“用户”。
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/create_aaduser_03.png) 
4. 若要打开“添加用户”对话框，请在底部工具栏中单击“添加用户”。 
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/create_aaduser_04.png) 
5. 在“告诉我们有关此用户的信息”对话框页上，执行以下步骤： 
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/create_aaduser_05.png) 
  1. 在“用户类型”中，选择“你的组织中的新用户”。  
  2. 在“用户名”文本框中，键入“BrittaSimon”。
  3. 单击“资源组名称” 的 Azure 数据工厂。
6. 在“用户配置文件”对话框页上，执行以下步骤： 
   
   ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/create_aaduser_06.png)  
  1. 在“名字”文本框中，键入“Britta”。  
  2. 在“姓氏”文本框中，键入“Simon”。
  3. 在“显示名称”文本框中，键入“Britta Simon”。
  4. 在“角色”列表中，选择“用户”。
  5. 单击“资源组名称” 的 Azure 数据工厂。
7. 在“获取临时密码”对话框页上，单击“创建”。
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/create_aaduser_07.png) 
8. 在“获取临时密码”对话框页上，执行以下步骤：
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/create_aaduser_08.png) 
  1. 写下“新密码”的值  
  2. 单击“完成”。   

### <a name="create-a-statuspage-test-user"></a>创建 StatusPage 测试用户
本部分的目的是在 StatusPage 中创建名为“Britta Simon”的用户。

StatusPage 支持实时预配。 已在[配置 Azure AD 单一登录](#configuring-azure-ad-single-single-sign-on)中启用它。

**若要在 StatusPage 中创建名为“Britta Simon”的用户，请执行以下步骤：**

1. 以管理员身份登录 StatusPage 公司站点。
2. 在顶部菜单中，单击“管理帐户”。
3. 单击“团队成员”选项卡。 
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_10.png) 
4. 单击“添加团队成员”。 
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_11.png) 
5. 将要预配的有效用户的**电子邮件地址**、**名字**和**姓氏**键入到相关文本框中。 
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_12.png) 
6. 选择“客户端管理员”作为**角色**。
7. 单击“创建帐户”。

### <a name="assign-the-azure-ad-test-user"></a>分配 Azure AD 测试用户
本部分的目的是通过授予 Britta Simon 访问 StatusPage 的权限，允许她使用 Azure SSO。

![分配用户][200] 

**若要将 Britta Simon 分配到 StatusPage，请执行以下步骤：**

1. 在 Azure 经典门户中，若要打开应用程序视图，请在目录视图的顶部菜单中，单击“应用程序”。
   
    ![分配用户][201] 
2. 在应用程序列表中，选择“StatusPage”。
   
    ![配置单一登录](./media/active-directory-saas-statuspage-tutorial/tutorial_statuspage_50.png) 
3. 在顶部菜单中，单击“用户”。
   
    ![分配用户][203] 
4. 在“用户”列表中，选择“Britta Simon”。
5. 在底部工具栏中，单击“分配”。
   
    ![分配用户][205]

### <a name="test-single-sign-on"></a>测试单一登录
本部分的目的是使用访问面板测试 Azure AD 单一登录配置。

单击访问面板中的“StatusPage”磁贴时，用户应自动登录到 StatusPage 应用程序。

## <a name="additional-resources"></a>其他资源
* [有关如何将 SaaS 应用与 Azure Active Directory 集成的教程列表](active-directory-saas-tutorial-list.md)
* [Azure Active Directory 的应用程序访问与单一登录是什么？](active-directory-appssoaccess-whatis.md)

<!--Image references-->

[1]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_04.png

[6]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_05.png
[10]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_06.png
[11]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_07.png
[20]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_201.png
[203]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_203.png
[204]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_204.png
[205]: ./media/active-directory-saas-statuspage-tutorial/tutorial_general_205.png







