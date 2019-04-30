---
title: TN054:使用 MFC DAO 类时直接调用 DAO
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.dao
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
ms.openlocfilehash: 938381f55b598911b69bb25bf7af576dfdfb2e4f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399650"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054:使用 MFC DAO 类时直接调用 DAO

> [!NOTE]
> 视觉对象C++环境和向导不支持 DAO （尽管 DAO 类包含并且仍可以使用它们）。 Microsoft 建议您使用[OLE DB 模板](../data/oledb/ole-db-templates.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)为新项目。 仅应在维护现有应用程序使用 DAO。

使用 MFC DAO 数据库类时，可能必须要直接使用 DAO 的情况。 通常情况下，这将不是这种情况，但 MFC 提供了一些帮助程序机制以便进行直接 DAO 调用简单时将使用 MFC 类与 DAO 的直接调用相结合。 进行直接的 DAO MFC 托管 DAO 对象的方法调用应需要仅几行代码。 如果需要创建和使用的 DAO 对象*不*由 MFC 管理，您将只需稍微复杂一点的实际调用`Release`对象上。 此技术说明介绍了你可能想要直接调用 DAO、 MFC 帮助程序可以如何帮助你，以及如何使用 DAO OLE 接口。 最后，此说明提供了显示如何 DAO 安全功能直接调用 DAO 一些示例函数。

## <a name="when-to-make-direct-dao-calls"></a>何时进行直接的 DAO 调用

在最常见的情况下进行直接调用 DAO 或时，集合需要刷新时要实现功能不使用 MFC 的包装。 由 MFC 不公开的最重要功能是安全性。 如果你想要实现安全功能，您需要直接使用的 DAO 个用户和组对象。 除了安全，有仅几个其他 DAO 功能不支持的 MFC。 其中包括记录集克隆和数据库复制功能，以及几个后期添加到 DAO。

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>DAO 和 MFC 的实现的简要概述

MFC 的 DAO 使使用 DAO 通过处理的许多细节，因此不需要担心在小的事情更轻松的换行。 这包括 OLE、 创建和管理的 DAO 对象 （尤其是集合对象），错误检查，并提供强类型化、 更简单的接口的初始化 (没有**VARIANT**或`BSTR`自变量）。 可以直接 DAO 呼叫并仍要利用这些功能。 你的代码必须做的全部操作是调用`Release`对于直接 DAO 所创建的任何对象调用并*不*修改任何 MFC 可能依赖于在内部接口指针。 例如，不要修改*m_pDAORecordset*成员的一种开放`CDaoRecordset`对象，除非你了解*所有*内部的后果。 但是，您可以使用*m_pDAORecordset*接口来调用 DAO 直接以获取字段集合。 在这种情况下*m_pDAORecordset*成员将不能修改。 您只需调用`Release`字段集合对象与对象完成后。

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>帮助程序以使 DAO 说明调用更容易

提供了可使调用 DAO 更轻松的帮助器是在 MFC DAO 数据库类在内部使用的同一个帮助器。 这些帮助程序用于检查返回代码时进行直接的 DAO 调用，检查预期错误，并引发相应异常，如有必要，日志记录调试输出。 有两个基础的 helper 函数，将映射到这两个帮助之一的四个宏。 只需读取的代码是最佳的说明。 请参阅**DAO_CHECK**， **DAO_CHECK_ERROR**， **DAO_CHECK_MEM**，以及**DAO_TRACE** AFXDAO 中。H，若要查看的宏，并查看**AfxDaoCheck**并**AfxDaoTrace** DAOCORE 中。CPP。

## <a name="using-the-dao-ole-interfaces"></a>使用 DAO OLE 接口

标头文件 DBDAOINT 中定义的 DAO 对象层次结构中每个对象的 OLE 接口。H，在 Visual Studio.NET 2003\VC7\include \Program Files\Microsoft 目录中找到。 这些接口提供使你可以操作整个 DAO 层次结构的方法。

对于许多 DAO 接口中的方法，您将需要处理`BSTR`对象 （长度前缀的字符串在 OLE 自动化中使用）。 `BSTR`对象通常封装在**变体**数据类型。 MFC 类`COleVariant`本身继承自**变体**数据类型。 具体取决于是否为 ANSI 或 Unicode 生成项目，DAO 接口将返回 ANSI 或 Unicode `BSTR`s。 两个宏，V_BSTR 和 V_BSTRT，可用于在确保 DAO 接口获取`BSTR`的预期类型。

将提取 V_BSTR *bstrVal*的成员`COleVariant`。 当您需要传递的内容时，通常使用此宏`COleVariant`DAO 接口的方法。 下面的代码段显示了声明和实际使用的 DAO DAOUser 接口充分利用 V_BSTR 宏的两个方法：

```cpp
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

请注意，`VT_BSTRT`参数中指定`COleVariant`构造函数更高版本可确保将采用 ANSI`BSTR`中`COleVariant`如果构建的应用程序和 Unicode 的 ANSI 版本`BSTR`Unicode 版本的你的应用程序。 这是 DAO 的需要。

其他宏，V_BSTRT，将提取的 ANSI 或 Unicode *bstrVal*的成员`COleVariant`具体取决于生成 （ANSI 或 Unicode） 类型。 下面的代码演示如何提取`BSTR`值从`COleVariant`到`CString`:

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

V_BSTRT 宏，以及其他方法来打开存储在其他类型`COleVariant`，DAOVIEW 示例所示。 具体而言，在执行此转换`CCrack::strVARIANT`方法。 此方法，如有可能，将转换的值`COleVariant`的实例到`CString`。

## <a name="simple-example-of-a-direct-call-to-dao"></a>直接调用 DAO 的简单示例

需要刷新基础 DAO 集合对象时，可能会出现的情况。 通常情况下，这应该不是有必要，但如有必要，它是一个简单过程。 要刷新可能需要集合的一个示例是在多用户环境中具有多个用户创建新 tabledefs 操作时。 在这种情况下 tabledefs 集合可能会变得陈旧。 若要刷新集合，只需调用`Refresh`特定集合对象并检查是否有错误的方法：

```cpp
DAO_CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

请注意，目前所有 DAO 集合对象接口的 MFC DAO 数据库类的未记录的实现详细信息。

## <a name="using-dao-directly-for-dao-security-features"></a>使用 DAO 直接用于 DAO 的安全功能

MFC DAO 数据库类不换行 DAO 安全功能。 您必须调用 DAO 的接口来使用某些 DAO 安全功能的方法。 下面的函数设置的系统数据库，然后将更改用户的密码。 此函数将调用其他三个随后定义的函数。

```cpp
void ChangeUserPassword()
{
    // Specify path to the Microsoft Access *// system database
    CString strSystemDB =
        _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

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
    // have no effect.
    SetSystemDB(strSystemDB);

    // User name and password manually added
    // by using Microsoft Access
    CString strUserName = _T("NewUser");
    CString strOldPassword = _T("Password");
    CString strNewPassword = _T("NewPassword");

    // Set default user so that MFC will be able
    // to log in by default using the user name and
    // password from the system database
    SetDefaultUser(strUserName, strOldPassword);

    // Change the password. You should be able to
    // call this function from anywhere in your
    // MFC application
    ChangePassword(strUserName, strOldPassword, strNewPassword);

    // ...
}
```

接下来的四个示例演示了如何：

- 设置系统 DAO 数据库 (。MDW 文件）。

- 设置默认用户和密码。

- 更改用户的密码。

- 更改的密码。MDB 文件。

### <a name="setting-the-system-database"></a>系统数据库设置

下面是示例函数将由应用程序将系统数据库设置。 进行任何其他 DAO 调用之前，必须调用此函数。

```cpp
// Set the system database that the
// DAO database engine will use

void SetSystemDB(CString& strSystemMDB)
{
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

    // Initialize DAO for MFC
    AfxDaoInit();
    DAODBEngine* pDBEngine = AfxDaoGetEngine();

    ASSERT(pDBEngine != NULL);

    // Call put_SystemDB method to set the *// system database for DAO engine
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));
}
```

### <a name="setting-the-default-user-and-password"></a>设置默认用户和密码

若要设置的默认用户和系统数据库的密码，请使用以下函数：

```cpp
void SetDefaultUser(CString& strUserName,
    CString& strPassword)
{
    COleVariant varUserName(strUserName, VT_BSTRT);
    COleVariant varPassword(strPassword, VT_BSTRT);

    DAODBEngine* pDBEngine = AfxDaoGetEngine();
    ASSERT(pDBEngine != NULL);

    // Set default user:
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

    // Set default password:
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));
}
```

### <a name="changing-a-users-password"></a>更改用户的密码

若要更改用户的密码，请使用以下函数：

```cpp
void ChangePassword(CString &strUserName,
    CString &strOldPassword,
    CString &strNewPassword)
{
    // Create (open) a workspace
    CDaoWorkspace wsp;
    CString strWspName = _T("Temp Workspace");

    wsp.Create(strWspName, strUserName, strOldPassword);
    wsp.Append();

    // Determine how many objects there are *// in the Users collection
    short nUserCount;
    short nCurrentUser;
    DAOUser *pUser = NULL;
    DAOUsers *pUsers = NULL;

    // Side-effect is implicit OLE AddRef()
    // on DAOUser object:
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

    // Side-effect is implicit OLE AddRef()
    // on DAOUsers object
    DAO_CHECK(pUsers->getcount(&nUserCount));

    // Traverse through the list of users
    // and change password for the userid
    // used to create/open the workspace
    for(nCurrentUser = 0; nCurrentUser <nUserCount; nCurrentUser++)
    {
        COleVariant varIndex(nCurrentUser, VT_I2);
        COleVariant varName;

        // Retrieve information for user nCurrentUser
        DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

        // Retrieve name for user nCurrentUser
        DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

        CString strTemp = V_BSTRT(&varName);

        // If there is a match, change the password
        if (strTemp == strUserName)
        {
            COleVariant varOldPwd(strOldPassword, VT_BSTRT);
            COleVariant varNewPwd(strNewPassword, VT_BSTRT);

            DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd),
                V_BSTR(&varNewPwd)));

            TRACE("\t Password is changed\n");
        }
    }
    // Clean up: decrement the usage count
    // on the OLE objects
    pUser->Release();
    pUsers->Release();
    wsp.Close();
}
```

### <a name="changing-the-password-of-an-mdb-file"></a>更改的密码。MDB 文件

若要更改的密码。MDB 文件，请使用以下函数：

```cpp
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)
{
    CDaoDatabase db;
    CString strConnect(_T(";pwd="));

    // the database must be opened as exclusive
    // to set a password
    db.Open(pDB, TRUE, FALSE, strConnect + pszOldPassword);

    COleVariant NewPassword(pszNewPassword, VT_BSTRT),
                OldPassword(pszOldPassword, VT_BSTRT);

    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword),
        V_BSTR(&NewPassword)));

    db.Close();
}
```

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
