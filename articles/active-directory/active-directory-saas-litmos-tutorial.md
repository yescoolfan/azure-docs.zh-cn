---
title: "教程：Azure Active Directory 与 Litmos 的集成 | Microsoft Docs"
description: "了解如何在 Azure Active Directory 和 Litmos 之间配置单一登录。"
services: active-directory
documentationcenter: 
author: jeevansd
manager: femila
editor: 
ms.assetid: cfaae4bb-e8e5-41d1-ac88-8cc369653036
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/03/2017
ms.author: jeedes
ms.translationtype: Human Translation
ms.sourcegitcommit: c785ad8dbfa427d69501f5f142ef40a2d3530f9e
ms.openlocfilehash: 2c967d759806b47862179ecf9e9a89801134192a
ms.contentlocale: zh-cn
ms.lasthandoff: 05/26/2017


---
# <a name="tutorial-azure-active-directory-integration-with-litmos"></a>教程：Azure Active Directory 与 Litmos 的集成
本教程的目的是展示如何将 Litmos 与 Azure Active Directory (Azure AD) 进行集成。  

将 Litmos 与 Azure AD 集成可提供以下优势： 

* 可以在 Azure AD 中控制谁有权访问 Litmos 
* 可以让用户使用其 Azure AD 帐户自动登录到 Litmos 单一登录 (SSO)
* 可以在一个中心位置（即 Azure Active Directory）管理帐户 

如果想要了解有关 SaaS 应用与 Azure AD 集成的详细信息，请参阅 [What is application access and single sign-on with Azure Active Directory](active-directory-appssoaccess-whatis.md)（什么是使用 Azure Active Directory 的应用程序访问和单一登录）。

## <a name="prerequisites"></a>先决条件
若要配置 Azure AD 与 Litmos 的集成，需要具有以下项：

* Azure AD 订阅
* 启用了 Litmos 单一登录的订阅

>[!NOTE]
>测试本教程中的步骤时，建议不要使用生产环境。
> 

测试本教程中的步骤应遵循以下建议：

* 除非必要，请勿使用生产环境。
* 如果没有 Azure AD 试用环境，可以在[此处](https://azure.microsoft.com/pricing/free-trial/)获取一个月的试用版。 

## <a name="scenario-description"></a>方案描述
本教程的目的是介绍如何在测试环境中测试 Azure AD 单一登录。  

本教程中概述的方案包括三个主要构建基块：

1. 从库中添加 Litmos 
2. 配置和测试 Azure AD 单一登录

## <a name="add-litmos-from-the-gallery"></a>从库中添加 Litmos
若要配置 Litmos 与 Azure AD 的集成，需要从库中将 Litmos 添加到托管 SaaS 应用列表。

**若要从库中添加 Litmos，请执行以下步骤：**

1. 在 **Azure 经典门户**中，在左侧导航窗格上，单击“Active Directory”。 
   
    ![Active Directory][1]
2. 从“目录”列表中，选择要为其启用目录集成的目录。
3. 若要打开应用程序视图，请在目录视图的顶部菜单中，单击“应用程序”。
   
    ![应用程序][2]
4. 在页面底部单击“添加”。
   
    ![应用程序][3]
5. 在“要执行什么操作”对话框中，单击“从库中添加应用程序”。
   
    ![应用程序][4]
6. 在搜索框中，键入“Litmos”。
   
    ![应用程序][5]
7. 在结果窗格中，选择“Litmos”，然后单击“完成”以添加该应用程序。
   
    ![应用程序][500]

## <a name="configuring-and-testing-azure-ad-single-sign-on"></a>配置并测试 Azure AD 单一登录
本部分的目的是基于名为“Britta Simon”的测试用户展示如何配置并测试 Litmos 的 Azure AD 单一登录。

若要运行单一登录，Azure AD 需要知道与 Azure AD 用户相对应的 Litmos 用户。 换句话说，需要在 Azure AD 用户与 Litmos 中的相关用户之间建立链接关系。  

可以通过将 Azure AD 中“用户名”的值分配为 Litmos 中“用户名”的值来建立此链接关系。

若要配置并测试 Litmos 的 Azure AD 单一登录，需要完成以下构建基块：

1. **[配置 Azure AD 单一登录](#configuring-azure-ad-single-single-sign-on)** - 使用户能够使用此功能。
2. **[创建 Azure AD 测试用户](#creating-an-azure-ad-test-user)** - 使用 Britta Simon 测试 Azure AD 单一登录。
3. **[创建 Litmos 测试用户](#creating-a-halogen-software-test-user)** - 在 Litmos 中创建对应的 Britta Simon 用户，该用户链接到她的 Azure AD 用户。
4. **[分配 Azure AD 测试用户](#assigning-the-azure-ad-test-user)** - 使 Britta Simon 能够使用 Azure AD 单一登录。
5. **[测试单一登录](#testing-single-sign-on)** - 验证配置是否正常工作。

### <a name="configure-azure-ad-single-sign-on"></a>配置 Azure AD 单一登录
本部分的目的是在 Azure 经典门户中启用 Azure AD 单一登录并在 Litmos 应用程序中配置单一登录。  

在此过程中，需要创建 base-64 编码的证书文件。  

如果不熟悉此过程，请参阅[如何将二进制证书转换为文本文件](http://youtu.be/PlgrzUZ-Y1o)。

在配置过程中，需要为 Litmos 应用程序自定义 **SAML 令牌属性**。  

![Azure AD 单一登录][17] 

**若要配置 Litmos 的 Azure AD 单一登录，请执行以下步骤：**

1. 在 Azure AD 经典门户中，在 **Litmos** 应用程序集成页上，单击“配置单一登录”，以打开“配置单一登录”对话框。
   
    ![配置单一登录][6] 
2. 在“你希望用户如何登录到 Litmos”页上，选择“Azure AD 单一登录”，然后单击“下一步”。
   
    ![Azure AD 单一登录][7] 
3. 以管理员身份登录到你的 Litmos 公司站点（例如：*https://azureapptest.litmos.com/account/Login*）。
   
    ![Azure AD 单一登录][21] 
4. 在左侧导航栏中，单击“帐户”。
   
    ![Azure AD 单一登录][22] 
5. 单击“集成”选项卡。
   
    ![Azure AD 单一登录][23] 
6. 在“集成”选项卡上，向下滚动到“第三方集成”，然后单击“SAML 2.0”选项卡。
   
    ![Azure AD 单一登录][24] 
7. 复制“Litmos 的 SAML 终结点是:”下的值。
   
    ![Azure AD 单一登录][26] 
8. 在 Azure 经典门户中，在“配置应用设置”对话框页上，执行以下步骤：
   
    ![Azure AD 单一登录][8] 
   
    1. 在“标识符”文本框中，键入用户用来登录 Litmos 应用程序的 URL（例如：*https://azureapptest.litmos.com/account/Login*）。
   
    2. 在“回复 URL”文本框中，粘贴你在上一步骤中从 Litmos 应用程序复制的值。
   
    3. 单击“下一步”。
9. 在“在 Litmos 处配置单一登录”页上，执行以下步骤：
   
    ![Azure AD 单一登录][2] 
   
    * 单击“下载证书”，然后将文件保存在计算机上。
10. 在 **Litmos** 应用程序中，执行以下步骤：
    
     ![Azure AD 单一登录][25] 
    
     1. 单击“启用 SAML”。
    
     2. 基于下载的证书创建一个 **base-64 编码**的文件。  
    >[!TIP]
    >有关详细信息，请参阅 [How to convert a binary certificate into a text file](http://youtu.be/PlgrzUZ-Y1o)（如何将二进制证书转换为文本文件）。
     >

     3. 在记事本中打开 base-64 编码证书，将其内容复制到剪贴板，然后再粘贴到“SAML X.509 证书”文本框中。
    
     4. 单击“保存更改”。
11. 在 Azure AD 经典门户中，选择“单一登录配置确认”，然后单击“下一步”。 
    
     ![Azure AD 单一登录][10]
12. 在“单一登录确认”页上，单击“完成”。  
    
     ![Azure AD 单一登录][11]
13. 在顶部菜单中，单击“属性”以打开“SAML 令牌属性”对话框。 
    
    ![配置单一登录][12]
14. 在“添加用户属性”对话框中，执行以下步骤： 
    
    ![配置单一登录][14]
    
    | 属性名称 | 属性值 |
    | --- | --- |
    | Email |user.mail |
    | FirstName |user.givenname |
    | LastName |user.surname |
    
    对于上表中的每个数据行，执行以下步骤：
    
 1. 单击“添加用户属性”。    
   ![配置单一登录][15]
 2. 在“属性名称”文本框中，键入为该行显示的**属性名称**。
 3. 选择为该行显示的**属性值**。
 4. 单击“完成”以关闭“添加用户属性”对话框。


1. 单击“应用更改”。 
   
   ![配置单一登录][16]

### <a name="create-an-azure-ad-test-user"></a>创建 Azure AD 测试用户
本部分的目的是在 Azure 经典门户中创建名为 Britta Simon 的测试用户。  

![创建 Azure AD 用户][20]

**若要在 Azure AD 中创建测试用户，请执行以下步骤：**

1. 在 **Azure 经典门户**中，在左侧导航窗格上，单击“Active Directory”。
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-litmos-tutorial/create_aaduser_09.png)  
2. 在“目录”列表中，选择要启用目录集成的目录。
3. 若要显示用户列表，请在顶部菜单中，单击“用户”。
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-litmos-tutorial/create_aaduser_03.png) 
4. 若要打开“添加用户”对话框，请在底部工具栏中单击“添加用户”。 
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-litmos-tutorial/create_aaduser_04.png) 
5. 在“告诉我们有关此用户的信息”对话框页上，执行以下步骤： 
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-litmos-tutorial/create_aaduser_05.png)  
   
    1. 对于“用户类型”，选择“组织中的新用户”。
   
    2. 在“用户名”文本框中，键入“BrittaSimon”。
   
    3. 单击“下一步”。
6. 在“用户配置文件”对话框页上，执行以下步骤： 
   
   ![创建 Azure AD 测试用户](./media/active-directory-saas-litmos-tutorial/create_aaduser_06.png) 
   
   1. 在“名字”文本框中，键入“Britta”。  
   
   2. 在“姓氏”文本框中，键入“Simon”。
   
   3. 在“显示名称”文本框中，键入“Britta Simon”。
   
   4. 在“角色”列表中，选择“用户”。
   5. 单击“下一步”。
7. 在“获取临时密码”对话框页上，单击“创建”。
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-litmos-tutorial/create_aaduser_07.png) 
8. 在“获取临时密码”对话框页上，执行以下步骤：
   
    ![创建 Azure AD 测试用户](./media/active-directory-saas-litmos-tutorial/create_aaduser_08.png) 
   
    1. 写下“新密码”的值。
   
    2. 单击“完成”。   

### <a name="create-a-litmos-test-user"></a>创建 Litmos 测试用户
本部分的目的是在 Litmos 中创建名为 Britta Simon 的用户。  
Litmos 应用程序支持实时预配。 这意味着，在尝试使用访问面板访问应用程序期间，如有必要，将会自动创建一个用户帐户。

**若要在 Litmos 中创建名为 Britta Simon 的用户，请执行以下步骤：**

1. 以管理员身份登录到你的 Litmos 公司站点（例如：*https://azureapptest.litmos.com/account/Login*）。
   
    ![Azure AD 单一登录][21] 
2. 在左侧导航栏中，单击“帐户”。
   
    ![Azure AD 单一登录][22] 
3. 单击“集成”选项卡。
   
    ![Azure AD 单一登录][23] 
4. 在“集成”选项卡上，向下滚动到“第三方集成”，然后单击“SAML 2.0”选项卡。
   
    ![Azure AD 单一登录][24] 
5. 选择“自动生成用户:”。
   
    ![Azure AD 单一登录][27] 

### <a name="assign-the-azure-ad-test-user"></a>分配 Azure AD 测试用户
本部分的目的是通过向 Britta Simon 授予对 Litmos 的访问权限，使她能够使用 Azure 单一登录。

![分配用户][200] 

**若要将 Britta Simon 分配到 Litmos，请执行以下步骤：**

1. 在 Azure 经典门户中，若要打开应用程序视图，请在目录视图的顶部菜单中，单击“应用程序”。
   
    ![分配用户][201] 
2. 在应用程序列表中，选择“Litmos”。
   
    ![分配用户][202] 
3. 在顶部菜单中，单击“用户”。
   
    ![分配用户][203] 
4. 在“用户”列表中，选择“Britta Simon”。
5. 在底部工具栏中，单击“分配”。
   
    ![分配用户][205]

### <a name="test-single-sign-on"></a>测试单一登录
本部分的目的是使用访问面板测试 Azure AD 单一登录配置。  

当在访问面板中单击 Litmos 磁贴时，应当会自动登录到 Litmos 应用程序。

## <a name="additional-resources"></a>其他资源
* [有关如何将 SaaS 应用与 Azure Active Directory 集成的教程列表](active-directory-saas-tutorial-list.md)
* [Azure Active Directory 的应用程序访问与单一登录是什么？](active-directory-appssoaccess-whatis.md)

<!--Image references-->

[1]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_04.png
[5]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_01.png
[500]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_02.png

[6]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_05.png
[7]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_03.png
[8]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_04.png
[9]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_05.png
[10]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_06.png
[11]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_07.png
[12]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_80.png
[13]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_81.png
[14]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_82.png
[15]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_81.png
[16]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_19.png
[17]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_67.png


[20]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_100.png
[21]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_60.png
[22]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_61.png
[23]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_62.png
[24]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_63.png
[25]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_64.png
[26]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_65.png
[27]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_66.png

[200]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_68.png
[203]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_203.png
[204]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_204.png
[205]: ./media/active-directory-saas-litmos-tutorial/tutorial_general_205.png


[400]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_400.png
[401]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_401.png
[402]: ./media/active-directory-saas-litmos-tutorial/tutorial_litmos_402.png






