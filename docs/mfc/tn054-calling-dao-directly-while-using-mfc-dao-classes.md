---
title: "TN054：使用 MFC DAO 类时直接调用 DAO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.dao"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO（数据访问对象）, 和 MFC"
  - "DAO（数据访问对象）, 直接调用"
  - "DAO（数据访问对象）, 安全性"
  - "MFC [C++], DAO 和"
  - "密码 [C++], 调用 DAO"
  - "安全性 [MFC]"
  - "安全性 [MFC], DAO"
  - "TN054"
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# TN054：使用 MFC DAO 类时直接调用 DAO
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  从 Visual C\+\+ .NET 起，Visual C\+\+ 环境和向导不再支持 DAO（不过提供了 DAO 类，仍可供您使用）。  Microsoft 建议对新项目使用 [OLE DB 模板](../data/oledb/ole-db-templates.md) 或 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)。  DAO 只应用于维护现有的应用程序。  
  
 当使用 MFC 数据库类 DAO 时，可能会直接使用 DAO 的情况是必需的。  通常，这不需要，但是，MFC 提供了一些帮助程序机制实现直接调用 DAO 电话简单，在组合使用 MFC 类直接使用 DAO 时调用。  对一个 MFC DAO 托管对象的方法直接调用 DAO 应只需要几行代码。  如果需要创建和使用 MFC DAO 不受托管对象，则必须通过实际调用对象的 **发布** 内容完成更多工作。  此技术声明解释何时可能需要直接调用 DAO，所以 MFC 的帮助程序可以完成帮助您和 DAO 如何使用 OLE 接口。  最后，此注释提供演示如何的一些示例函数直接调用 DAO DAO 安全功能的。  
  
## 何时直接调用 DAO 调用  
 直接调用 DAO 调用的最常见情况发生，则该集合需要刷新，或当您实现 MFC 时不是包装的功能。  MFC 不公开的最重要的功能是安全性。  如果要实现安全功能，您将需要使用 DAO，用户和组直接对象。  除了安全外，不具有 MFC DAO 只支持的某些功能。  这些包含记录集克隆和同步数据库复制功能以及一些将延迟到 DAO。  
  
## DAO 和 MFC 实现的概述  
 MFC DAO 的包装使使用 DAO 轻松地处理许多细节，因此您无需担心小的任务。  这包含强类型，简单接口的初始化的 OLE、DAO 创建和管理对象 \(尤其是\)，集合对象错误检查和提供 \(无 **VARIANT** 或 `BSTR` 参数。\)  可以直接调用 DAO 电话和仍利用这些功能。  所有代码必须执行是直接调用 DAO 调用创建的任何对象 \( **发布** 和不修改任何 MFC 接口指针可以在内部依赖于。  例如，在中，除非您了解 *所有* 内部细节，请勿修改开放式 `CDaoRecordset` 对象的 **m\_pDAORecordset** 成员。  但是，使用 **m\_pDAORecordset** 接口，您可以直接调用 DAO 获取字段集合。  在这种情况下不修改 **m\_pDAORecordset** 成员。  在使用完对象时，必须调用字段集合对象的 **发布**。  
  
## DAO 使调用更简单的帮助程序的说明  
 帮助提供程序进行调用 DAO 更易于被内部在 MFC DAO 数据库类使用相同的帮助器。  这些帮助器用于检查返回代码，当调用一次，直接调用 DAO 记录时调试输出，如有必要，检查和预期错误引发相应的异常。  映射到具有这两个帮助程序之一的基础两个 Helper 函数和四宏。  最佳的说明是读取代码。  请参见 **DAO\_CHECK**、**DAO\_CHECK\_ERROR**、**DAO\_CHECK\_MEM**和 **DAO\_TRACE** 中 AFXDAO.H 查看宏，并了解 **AfxDaoCheck** 和 **AfxDaoTrace** 位于 DAOCORE.CPP。  
  
## 使用 DAO OLE 接口  
 每个对象创建 OLE 接口 DAO 在对象层次结构在头文件 DBDAOINT.H 定义，在\\Program Files\\Microsoft Visual Studio.NET 2003\\VC 7 \\ include 找到目录。  这些接口提供使您可以操作整个 DAO 层次结构的方法。  
  
 很多在 DAO 接口的方法，则需要处理 `BSTR` 对象 \(用于 OLE 自动化的长度为前缀的字符串\)。  `BSTR` 对象。**VARIANT** 数据类型通常中封装。  MFC 类 `COleVariant` 从 **VARIANT** 继承数据类型。  根据是否生成 ANSI 或 Unicode 项目，DAO 接口将返回 `BSTR`。ANSI 或 Unicode。  两宏，**V\_BSTR** 和 **V\_BSTRT**，用于确保是有用的 DAO 接口获取所需类型的 `BSTR`。  
  
 **V\_BSTR** 中提取 `COleVariant`的 **bstrVal** 成员。  此宏，如果需要传递 `COleVariant` 的内容。DAO 接口的方法时，通常由使用。  下面的代码段说明声明和实际使用利用 **V\_BSTR** 宏 DAOUser DAO 的两个方法的接口：  
  
```  
COleVariant varOldName;  
COleVariant varNewName( _T("NewUser"), VT_BSTRT );  
  
// Code to assign pUser to a valid value omitted  
DAOUser *pUser = NULL;  
  
// These method declarations were taken from DBDAOINT.H  
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;  
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;  
  
DAO_CHECK( pUser->get_Name( &V_BSTR ( &varOldName ) ));  
DAO_CHECK( pUser->put_Name( V_BSTR ( &varNewName ) ));  
```  
  
 注意 `COleVariant` 构造函数的 `VT_BSTRT` 参数确保在 `COleVariant` 上面的 ANSI `BSTR`，如果要生成应用的 ANSI 版本和 Unicode 应用程序 `BSTR` 的 Unicode 版本。  这是" DAO 需要。  
  
 其他宏，**V\_BSTRT**，根据生成类型中提取 ANSI 或 Unicode `COleVariant` 的 **bstrVal** 成员 \(ANSI 或 Unicode。\)  下面的代码演示如何从 `COleVariant` 中提取 `BSTR` 值到 `CString`:  
  
```  
COleVariant varName( _T( "MyName" ), VT_BSTRT );  
CString str = V_BSTRT( &varName );  
```  
  
 **V\_BSTRT** 宏，以及打开 `COleVariant`存储其他类型的其他方法一起，在 DAOVIEW 示例中演示。  具体而言，此转换将 **CCrack::strVARIANT** 方法执行。  此方法，如果可能，将 `COleVariant` 的值转换为 `CString`实例。  
  
## 一个直接调用的简单示例对 DAO 的  
 刷新，则基础 DAO 集合对象时，需要的情况可能出现。  通常，这应不是必需的，但是，它是一个简单的过程，则是必需的。  例如，如果集合可能需要刷新是，当运行在与创建新的 tabledefs 时的多个用户的多用户环境。  在这种情况下 tabledefs 集合可能过时。  若要刷新集合，则需要调用特定集合对象的 **刷新** 和方法检查错误：  
  
```  
DAO_CHECK( pMyDaoDatabase->  
    m_pDAOTableDefs->Refresh( ) );  
```  
  
 请注意集合对象当前所有 DAO 接口是 MFC 数据库类 DAO 的使用未证明的执行详细信息。  
  
## 使用 DAO 直接的 DAO 安全功能  
 MFC 数据库类 DAO 不包装 DAO 安全功能。  必须调用 DAO 接口方法重用 DAO 安全功能。  以下函数将系统数据库将更改用户的密码。  此函数调用其他三个函数中，后面定义。  
  
```  
void ChangeUserPassword( )  
{  
   // Specify path to the Microsoft Access  
   // system database  
   CString strSystemDB =   
     _T( "c:\\Program Files\\MSOffice\\access\\System.mdw" );  
  
   // Set system database before MFC initilizes DAO  
   // NOTE: An MFC module uses only one instance   
   // of a DAO database engine object. If you have   
   // called a DAO object in your application prior   
   // to calling the function below, you must call   
   // AfxDaoTerm to destroy the existing database   
   // engine object. Otherwise, the database engine   
   // object already in use will be reused, and setting  
   // a system datbase will have no effect.  
   //  
   // If you have used a DAO object prior to calling   
   // this function it is important that DAO be   
   // terminated with AfxDaoTerm since an MFC  
   // module only gets one copy of the database engine   
   // and that engine will be reused if it hasn't been   
   // terminated. In other words, if you do not call   
   // AfxDaoTerm and there is currently a database   
   // initialized, setting the system database will   
   // have no affect.  
  
   SetSystemDB( strSystemDB );  
  
   // User name and password manually added  
   // by using Microsoft Access  
   CString strUserName = _T( "NewUser" );  
   CString strOldPassword = _T( "Password" );  
   CString strNewPassword = _T( "NewPassword" );  
  
   // Set default user so that MFC will be able  
   // to log in by default using the user name and   
   // password from the system database  
   SetDefaultUser( strUserName, strOldPassword );  
  
   // Change the password. You should be able to  
   // call this function from anywhere in your   
   // MFC application  
   ChangePassword( strUserName, strOldPassword,   
                   strNewPassword );  
  
   .  
   .  
   .  
  
}  
```  
  
 下面四个示例说明如何：  
  
-   设置系统 DAO 数据库 \(.MDW 文件\)。  
  
-   设置默认用户和密码。  
  
-   更改用户的密码。  
  
-   将 .mdb 文件的密码。  
  
### 设置系统数据库  
 下面的设置由应用程序使用的系统数据库的示例函数。  此函数，在其他任何 DAO 调用之前，必须调用。  
  
```  
// Set the system database that the   
// DAO database engine will use  
  
void SetSystemDB( CString & strSystemMDB )  
{  
   COleVariant varSystemDB( strSystemMDB, VT_BSTRT );  
  
   // Initialize DAO for MFC  
   AfxDaoInit( );  
   DAODBEngine* pDBEngine = AfxDaoGetEngine( );  
  
   ASSERT( pDBEngine != NULL );  
  
   // Call put_SystemDB method to set the   
   // system database for DAO engine  
   DAO_CHECK( pDBEngine->put_SystemDB( varSystemDB.bstrVal ) );  
}  
```  
  
### 设置默认用户和密码  
 若要设置默认用户和密码系统的数据库，请使用下列函数：  
  
```  
void SetDefaultUser(CString & strUserName, CString & strPassword)  
{  
  COleVariant varUserName( strUserName, VT_BSTRT );  
  COleVariant varPassword( strPassword, VT_BSTRT );  
  
  DAODBEngine* pDBEngine = AfxDaoGetEngine( );  
  ASSERT( pDBEngine != NULL );  
  
  // Set default user:  
  DAO_CHECK( pDBEngine->put_DefaultUser( varUserName.bstrVal ) );  
  
  // Set default password:  
  DAO_CHECK( pDBEngine->put_DefaultPassword( varPassword.bstrVal ) );  
}  
```  
  
### 更改用户的密码  
 若要更改用户密码，请使用下列函数：  
  
```  
void ChangePassword( CString &strUserName,   
                     CString &strOldPassword,   
                     CString &strNewPassword )  
{  
   // Create (open) a workspace  
   CDaoWorkspace wsp;  
   CString strWspName = _T( "Temp Workspace" );  
  
   wsp.Create( strWspName, strUserName,  
               strOldPassword );  
   wsp.Append( );  
  
   // Determine how many objects there are  
   // in the Users collection  
   short nUserCount;  
   short nCurrentUser;  
   DAOUser *pUser  = NULL;  
   DAOUsers *pUsers = NULL;  
  
   // Side-effect is implicit OLE AddRef( )   
   // on DAOUser object:  
   DAO_CHECK( wsp.m_pDAOWorkspace->get_Users( &pUsers ) );  
  
   // Side-effect is implicit OLE AddRef( )   
   // on DAOUsers object  
    DAO_CHECK( pUsers->get_Count( &nUserCount ) );  
  
   // Traverse through the list of users   
   // and change password for the userid  
   // used to create/open the workspace  
   for( nCurrentUser = 0; nCurrentUser < nUserCount;  
        nCurrentUser++ )  
   {  
       COleVariant varIndex( nCurrentUser, VT_I2 );  
       COleVariant varName;  
  
       // Retrieve information for user nCurrentUser  
       DAO_CHECK( pUsers->get_Item( varIndex, &pUser ) );  
  
       // Retrieve name for user nCurrentUser  
       DAO_CHECK( pUser->get_Name( &V_BSTR( &varName ) ) );  
  
       CString strTemp = V_BSTRT( &varName );  
  
       // If there is a match, change the password  
       if( strTemp == strUserName )  
       {  
           COleVariant varOldPwd( strOldPassword,   
                                  VT_BSTRT );  
           COleVariant varNewPwd( strNewPassword,   
                                  VT_BSTRT );  
  
           DAO_CHECK( pUser->NewPassword( V_BSTR( &varOldPwd ),  
                      V_BSTR( &varNewPwd ) ) );  
  
           TRACE( "\t Password is changed\n" );  
       }  
   }  
  
   // Clean up: decrement the usage count  
   // on the OLE objects  
   pUser->Release( );  
   pUsers->Release( );  
  
   wsp.Close( );  
}  
```  
  
### 将 .mdb 文件的密码  
 若要更改 .mdb 文件的密码，请使用下列函数：  
  
```  
void SetDBPassword( LPCTSTR pDB, LPCTSTR pszOldPassword, LPCTSTR pszNewPassword )  
{  
   CDaoDatabase db;  
   CString strConnect( _T( ";pwd=" ) );  
  
   // the database must be opened as exclusive  
   // to set a password  
   db.Open( pDB, TRUE, FALSE,   
            strConnect + pszOldPassword );  
  
   COleVariant NewPassword( pszNewPassword, VT_BSTRT ),  
               OldPassword( pszOldPassword, VT_BSTRT );  
  
   DAO_CHECK( db.m_pDAODatabase->NewPassword( V_BSTR( &OldPassword ),  
              V_BSTR( &NewPassword ) ) );  
  
   db.Close();  
}  
```  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)