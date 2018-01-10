---
title: "TN054： 使用 MFC DAO 类时直接调用 DAO |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.dao
dev_langs: C++
helpviewer_keywords:
- MFC, DAO and
- passwords [MFC], calling DAO
- security [MFC], DAO
- DAO (Data Access Objects), calling directly
- DAO (Data Access Objects), security
- security [MFC]
- TN054
- DAO (Data Access Objects), and MFC
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de49cec931878cbfe06939269721b17a37a66202
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054：使用 MFC DAO 类时直接调用 DAO
> [!NOTE]
>  Visual c + + 环境和向导不支持 DAO （尽管 DAO 类包括并且仍可以使用它们）。 Microsoft 建议你使用[OLE DB 模板](../data/oledb/ole-db-templates.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)为新项目。 你只应在维护现有应用程序使用 DAO。  
  
 使用 MFC DAO 数据库类时，可能无法直接使用 DAO 所必需的情况。 通常情况下，这将不是这种情况，但 MFC 提供了一些帮助器机制，以方便进行直接 DAO 呼叫简单时的 MFC 类使用结合基于 DAO 的直接调用。 进行直接 DAO MFC 托管 DAO 对象的方法的调用应需要仅有几行代码。 如果你需要创建和使用的 DAO 对象*不*由 MFC 管理，您将需要通过实际调用做一些工作**版本**对象上。 此技术说明介绍当你可能想要直接调用 DAO、 MFC 帮助程序可以做什么来帮助你，以及如何使用 DAO OLE 接口。 最后，此说明提供显示如何为 DAO 安全功能直接调用 DAO 某些示例函数。  
  
## <a name="when-to-make-direct-dao-calls"></a>何时进行直接 DAO 调用  
 集合需要刷新时，将发生最常见的情形进行直接调用 DAO 或当你要实现不由 MFC 包装的功能。 最重要的功能没有公开的 MFC 是安全的。 如果你想要实现安全功能，你将需要直接使用的 DAO 用户和组对象。 安全，除了有仅几个其他 DAO 功能不支持的 MFC。 其中包括记录集克隆和数据库复制功能，以及少量后期添加到 DAO。  
  
## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>DAO 和 MFC 的实现的简要概述  
 MFC 的换行的 DAO 使得使用 DAO 通过处理的许多细节，因此无需担心很少的操作更容易。 这包括 OLE、 创建和管理的 DAO 对象 （尤其是集合对象），错误检查，并提供一个强类型、 更简单的界面的初始化 (没有**VARIANT**或`BSTR`自变量）。 你可以进行直接 DAO 调用，同时仍然可以利用这些功能。 你的代码必须做的全部操作是调用**版本**对于直接 DAO 所创建的任何对象调用和*不*修改任何 MFC 可能依赖于内部的接口指针。 例如，不要修改**m_pDAORecordset**打开成员`CDaoRecordset`对象除非你了解*所有*内部的后果。 但是，你可以使用**m_pDAORecordset**接口来调用 DAO 直接来获取字段集合。 在这种情况下**m_pDAORecordset**成员将不能修改。 你只需调用**版本**字段集合对象与对象完成后。  
  
## <a name="description-of-helpers-to-make-dao-calls-easier"></a>说明的帮助器以使 DAO 调用更容易  
 提供了可使调用 DAO 更轻松的帮助器是在 MFC DAO 数据库类中内部使用的同一个帮助器。 这些帮助器用于时进行直接的 DAO 调用，检查返回代码的预期错误检查和引发相应异常，如有必要日志记录调试输出。 有两个基础的 helper 函数和映射到这些两个帮助器之一的四个宏。 最佳的说明将只需阅读的代码。 请参阅**DAO_CHECK**， **DAO_CHECK_ERROR**， **DAO_CHECK_MEM**，和**DAO_TRACE** AFXDAO 中。若要查看的宏，并查看的 H **AfxDaoCheck**和**AfxDaoTrace** DAOCORE 中。CPP。  
  
## <a name="using-the-dao-ole-interfaces"></a>使用 DAO OLE 接口  
 标头文件 DBDAOINT 中定义的 DAO 对象层次结构中每个对象的 OLE 接口。H、 files\microsoft Visual Studio.NET 2003\VC7\include 目录中找到。 这些接口提供方法，使您可以操作整个 DAO 层次结构。  
  
 对于很多 DAO 接口中的方法中，你将需要操作`BSTR`对象 （长度为前缀的字符串在 OLE 自动化中使用）。 `BSTR`对象通常封装在**VARIANT**数据类型。 MFC 类`COleVariant`本身继承自**VARIANT**数据类型。 具体取决于是否为 ANSI 或 Unicode 生成项目，DAO 接口将返回 ANSI 或 Unicode `BSTR`s。 两个宏**V_BSTR**和**V_BSTRT**，可用于在确保 DAO 接口获取`BSTR`预期类型。  
  
 **V_BSTR**将提取**bstrVal**的成员`COleVariant`。 当你需要传递的内容时，通常使用此宏`COleVariant`到 DAO 接口方法。 下面的代码段显示了声明和实际用于两种方法可以充分利用的 DAO DAOUser 接口**V_BSTR**宏：  
  
```  
COleVariant varOldName;  
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

 
// Code to assign pUser to a valid value omitted  
DAOUser *pUser = NULL;  
 
// These method declarations were taken from DBDAOINT.H  
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;  
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;  
 
DAO_CHECK(pUser->get_Name(&V_BSTR (&varOldName)));

DAO_CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```  
  
 请注意，`VT_BSTRT`中指定的自变量`COleVariant`上述构造函数可确保将 ANSI`BSTR`中`COleVariant`如果生成你的应用程序和 Unicode 的 ANSI 版本`BSTR`Unicode 版本的你的应用程序。 这是 DAO 的期望。  
  
 其他宏， **V_BSTRT**，将提取的 ANSI 或 Unicode **bstrVal**的成员`COleVariant`具体取决于生成 （ANSI 或 Unicode） 类型。 下面的代码演示了如何提取`BSTR`值从`COleVariant`到`CString`:  
  
```  
COleVariant varName(_T("MyName"), VT_BSTRT);

CString str = V_BSTRT(&varName);
```  
  
 **V_BSTRT**宏，以及其他技术来打开存储在其他类型`COleVariant`，DAOVIEW 示例所示。 具体而言，在执行此转换**CCrack::strVARIANT**方法。 此方法，如有可能，将转换的值`COleVariant`到的实例`CString`。  
  
## <a name="simple-example-of-a-direct-call-to-dao"></a>直接调用 DAO 的简单示例  
 需要刷新基础 DAO 集合对象时，可能出现的情况。 通常情况下，这应不是必要的但它是一个简单的过程，如有必要。 集合可能需要刷新的一个示例是当了多个用户创建新 tabledefs 多用户环境中运行。 在这种情况下 tabledefs 集合可能会过时。 若要刷新集合，只需调用**刷新**特定集合对象并检查是否有错误的方法：  
  
```  
DAO_CHECK(pMyDaoDatabase->  
    m_pDAOTableDefs->Refresh());
```  
  
 请注意，当前所有 DAO 集合对象接口未记录的实现详细信息的 MFC DAO 数据库类。  
  
## <a name="using-dao-directly-for-dao-security-features"></a>使用 DAO 直接 DAO 安全功能  
 MFC DAO 数据库类不换行 DAO 安全功能。 必须调用方法的 DAO 接口，以便使用 DAO 的一些安全功能。 下面的函数设置系统数据库，然后将更改用户的密码。 此函数将调用其他三个随后定义的函数。  
  
```  
void ChangeUserPassword()  
{ *// Specify path to the Microsoft Access *// system database  
    CString strSystemDB = 
    _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

 *// Set system database before MFC initilizes DAO *// NOTE: An MFC module uses only one instance *// of a DAO database engine object. If you have *// called a DAO object in your application prior *// to calling the function below,
    you must call *// AfxDaoTerm to destroy the existing database *// engine object. Otherwise,
    the database engine *// object already in use will be reused,
    and setting *// a system datbase will have no effect. *// *// If you have used a DAO object prior to calling *// this function it is important that DAO be *// terminated with AfxDaoTerm since an MFC *// module only gets one copy of the database engine *// and that engine will be reused if it hasn't been *// terminated. In other words,
    if you do not call *// AfxDaoTerm and there is currently a database *// initialized,
    setting the system database will *// have no affect.  
 
    SetSystemDB(strSystemDB);

 *// User name and password manually added *// by using Microsoft Access  
    CString strUserName = _T("NewUser");

    CString strOldPassword = _T("Password");

    CString strNewPassword = _T("NewPassword");

 *// Set default user so that MFC will be able *// to log in by default using the user name and *// password from the system database  
    SetDefaultUser(strUserName,
    strOldPassword);

 *// Change the password. You should be able to *// call this function from anywhere in your *// MFC application  
    ChangePassword(strUserName,
    strOldPassword,   
    strNewPassword);

 
 .  
 .  
 .  
 
}  
```  
  
 接下来四个示例演示如何：  
  
-   设置系统 DAO 数据库 (。MDW 文件）。  
  
-   设置的默认用户和密码。  
  
-   更改用户的密码。  
  
-   更改的密码。MDB 文件。  
  
### <a name="setting-the-system-database"></a>设置系统数据库  
 下面是示例函数将设置应用程序将使用系统数据库。 进行任何其他 DAO 调用之前，必须调用此函数。  
  
```  
// Set the system database that the   
// DAO database engine will use  
 
void SetSystemDB(CString& strSystemMDB)  
{  
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

 *// Initialize DAO for MFC  
    AfxDaoInit();
DAODBEngine* pDBEngine = AfxDaoGetEngine();

 
    ASSERT(pDBEngine != NULL);

 *// Call put_SystemDB method to set the *// system database for DAO engine  
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));

} 
```  
  
### <a name="setting-the-default-user-and-password"></a>设置的默认用户和密码  
 若要设置的默认用户和系统数据库的密码，请使用以下函数：  
  
```  
void SetDefaultUser(CString& strUserName,
    CString& strPassword)  
{  
    COleVariant varUserName(strUserName,
    VT_BSTRT);

    COleVariant varPassword(strPassword,
    VT_BSTRT);

 
    DAODBEngine* pDBEngine = AfxDaoGetEngine();
ASSERT(pDBEngine != NULL);

 *// Set default user:  
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

 *// Set default password:  
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));

} 
```  
  
### <a name="changing-a-users-password"></a>更改用户的密码  
 若要更改用户的密码，请使用以下函数：  
  
```  
void ChangePassword(CString &strUserName,   
    CString &strOldPassword,   
    CString &strNewPassword)  
{ *// Create (open) a workspace  
    CDaoWorkspace wsp;  
    CString strWspName = _T("Temp Workspace");

 
    wsp.Create(strWspName, strUserName,  
    strOldPassword);

 wsp.Append();

 *// Determine how many objects there are *// in the Users collection  
    short nUserCount;  
    short nCurrentUser;  
    DAOUser *pUser = NULL;  
    DAOUsers *pUsers = NULL;  
 *// Side-effect is implicit OLE AddRef() *// on DAOUser object:  
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

 *// Side-effect is implicit OLE AddRef() *// on DAOUsers object  
    DAO_CHECK(pUsers->getcount(&nUserCount));

 *// Traverse through the list of users *// and change password for the userid *// used to create/open the workspace  
    for(nCurrentUser = 0; nCurrentUser <nUserCount;  
    nCurrentUser++) 
 {  
    COleVariant varIndex(nCurrentUser, VT_I2);

    COleVariant varName;  
 *// Retrieve information for user nCurrentUser  
    DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

 *// Retrieve name for user nCurrentUser  
    DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

 
    CString strTemp = V_BSTRT(&varName);

 *// If there is a match, change the password  
    if(strTemp == strUserName)  
 {  
    COleVariant varOldPwd(strOldPassword,   
    VT_BSTRT);

 COleVariant  varNewPwd(strNewPassword,   
    VT_BSTRT);

 
    DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd), 
    V_BSTR(&varNewPwd)));

 
    TRACE("\t Password is changed\n");

 }  
 }  
 *// Clean up: decrement the usage count *// on the OLE objects  
    pUser->Release();
pUsers->Release();

 
    wsp.Close();

} 
```  
  
### <a name="changing-the-password-of-an-mdb-file"></a>密码的更改。MDB 文件  
 若要更改的密码。MDB 文件，请使用以下函数：  
  
```  
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)  
{  
    CDaoDatabase db;  
    CString strConnect(_T(";pwd="));

 *// the database must be opened as exclusive *// to set a password  
    db.Open(pDB,
    TRUE,
    FALSE,   
    strConnect + pszOldPassword);

 
    COleVariant NewPassword(pszNewPassword,
    VT_BSTRT),  
    OldPassword(pszOldPassword,
    VT_BSTRT);

 
    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword), 
    V_BSTR(&NewPassword)));

 
    db.Close();

} 
```  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

