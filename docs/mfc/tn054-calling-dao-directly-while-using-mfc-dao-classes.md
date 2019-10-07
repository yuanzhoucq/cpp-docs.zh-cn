---
title: TN054：使用 MFC DAO 类时直接调用 DAO
ms.date: 09/17/2019
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
ms.openlocfilehash: cef9852f762a64579e11fe4b0d8606bfc9d36709
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095980"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054：使用 MFC DAO 类时直接调用 DAO

> [!NOTE]
> DAO 与 Access 数据库结合使用，并受 Office 2013 的支持。 3.6 是最终版本，被视为已过时。视觉对象C++环境和向导不支持 dao （尽管包含 dao 类，但你仍可以使用它）。 Microsoft 建议你将[OLE DB 模板](../data/oledb/ole-db-templates.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)用于新项目。 只应在维护现有应用程序时使用 DAO。

使用 MFC DAO 数据库类时，可能会出现需要直接使用 DAO 的情况。 通常情况下，不会出现这种情况，但 MFC 提供了一些 helper 机制，以便在结合使用 MFC 类和直接 DAO 调用时，使直接 DAO 调用更简单。 直接对 MFC 托管 DAO 对象的方法进行 DAO 调用时，只需编写几行代码。 如果需要创建并使用*不*由 MFC 管理的 DAO 对象，则必须通过对对象进行实际调用`Release`来完成一些工作。 本技术说明说明了当你可能想要直接调用 DAO 时，MFC 帮助器可以执行哪些操作来帮助你，以及如何使用 DAO OLE 接口。 最后，此注释提供一些示例函数，演示如何直接为 DAO 安全功能调用 DAO。

## <a name="when-to-make-direct-dao-calls"></a>何时进行直接 DAO 调用

当需要刷新集合或实现 MFC 未包装的功能时，进行直接 DAO 调用的最常见情况。 MFC 未公开的最重要功能是安全的。 如果要实现安全功能，您将需要直接使用 DAO 用户和组的对象。 除了安全性，MFC 还不支持其他几个 DAO 功能。 其中包括记录集克隆和数据库复制功能，以及一些到 DAO 的后期补充。

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>DAO 和 MFC 实现的简要概述

通过处理许多详细信息，DAO 包装的 DAO 使 DAO 的使用更加简单，因此您无需担心这些问题。 这包括： OLE 的初始化，创建和管理 DAO 对象（特别是集合对象），错误检查，并提供强类型的、更简单的接口（无**变体**或`BSTR`参数）。 您可以直接进行 DAO 调用，并且仍可以利用这些功能。 所有代码都必须为直接 DAO `Release`调用创建的任何对象调用，而*不*会修改 MFC 可能在内部依赖的任何接口指针。 例如，除非你了解*所有*内部后果，否则请不要`CDaoRecordset`修改开放式对象的*m_pDAORecordset*成员。 不过，您可以使用*m_pDAORecordset*接口直接调用 DAO 来获取字段集合。 在这种情况下，不会修改*m_pDAORecordset*成员。 使用完对象后， `Release`只需在 Fields 集合对象上调用。

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>简化 DAO 调用的帮助程序的说明

为了使调用 DAO 更简单，提供的帮助程序与在 MFC DAO 数据库类内部使用的帮助程序相同。 这些帮助程序用于在进行直接 DAO 调用时检查返回代码，记录调试输出，检查预期错误，并在必要时引发相应的异常。 有两个基础 helper 函数和四个宏映射到这两个帮助器中的一个。 最好的方法是阅读代码。 请参阅 AFXDAO 中的**DAO_CHECK**、 **DAO_CHECK_ERROR**、 **DAO_CHECK_MEM**和**DAO_TRACE** 。H 若要查看宏，请参阅**AfxDaoCheck** and **AfxDaoTrace** in DAOCORE.CPP.

## <a name="using-the-dao-ole-interfaces"></a>使用 DAO OLE 接口

DAO 对象层次结构中每个对象的 OLE 接口在标头文件 DBDAOINT 中定义。H，在 \Program Files\Microsoft Visual Studio .NET 2003 \ VC7\include 目录中。 这些接口提供允许您操作整个 DAO 层次结构的方法。

对于 DAO 接口中的许多方法，您需要操作一个`BSTR`对象（在 OLE 自动化中使用长度为前缀的字符串）。 对象通常封装在变量数据类型中。 `BSTR` MFC 类`COleVariant`本身继承自**变量**数据类型。 根据您是为 ansi 或 unicode 生成项目，DAO 接口将返回 ansi 或 unicode `BSTR`。 V_BSTR 和 V_BSTRT 两个宏有助于确保 DAO 接口获取`BSTR`预期类型的。

V_BSTR 将提取的*bstrVal*成员`COleVariant`。 当你需要将的内容`COleVariant`传递到 DAO 接口的方法时，通常使用此宏。 以下代码片段显示了使用 V_BSTR 宏的 DAO DAOUser 接口的两种方法的声明和实际用法：

```cpp
COleVariant varOldName;
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

// Code to assign pUser to a valid value omitted DAO 3.6 is the final version and it is considered obsolete.User *pUser = NULL;

// These method declarations were taken from DBDAOINT.H
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;
DAO 3.6 is the final version and it is considered obsolete._CHECK(pUser->get_Name(&V_BSTR (&varOldName))); DAO 3.6 is the final version and it is considered obsolete._CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```

`COleVariant` `BSTR` `COleVariant`请注意，在上面的构造函数中指定的`BSTR` 参数可确保如果生成应用程序的ansi版本和unicode版本的，将在中有ansi`VT_BSTRT`应用程序。 这正是 DAO 所期望的。

另一个宏 V_BSTRT 将提取 ANSI 或 unicode *bstrVal*成员`COleVariant` ，具体取决于生成的类型（ansi 或 unicode）。 下面的代码演示如何将`BSTR` `COleVariant`中的值提取到`CString`中：

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

DAOVIEW 示例演示了 V_BSTRT 宏以及用于打开存储在中`COleVariant`的其他类型的其他方法。 具体而言，此转换在`CCrack::strVARIANT`方法中执行。 如果可能，此方法会将的值`COleVariant`转换为的`CString`实例。

## <a name="simple-example-of-a-direct-call-to-dao"></a>直接调用 DAO 的简单示例

当需要刷新基础 DAO 集合对象时，可能会出现这种情况。 通常，这不是必需的，但它是一个简单的过程（如有必要）。 例如，在多个用户创建新 tabledefs 的多用户环境中操作时，可能需要刷新集合。 在这种情况下，tabledefs 收集可能会过时。 若要刷新集合，只需调用`Refresh`特定集合对象的方法并检查错误：

```cpp DAO 3.6 is the final version and it is considered obsolete._CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

请注意，当前所有 DAO 集合对象接口都是 MFC DAO 数据库类的未记录实现细节。

## <a name="using-dao-directly-for-dao-security-features"></a>直接将 DAO 用于 DAO 安全功能

MFC DAO 数据库类不包装 DAO 安全功能。 您必须调用 DAO 接口的方法才能使用某些 DAO 安全功能。 以下函数设置系统数据库，然后更改用户的密码。 此函数将调用其他三个函数，这些函数随后定义。

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

接下来的四个示例演示了如何执行以下操作：

- 设置系统 DAO 数据库（。MDW 文件）。

- 设置默认的 "用户" 和 "密码"。

- 更改用户的密码。

- 更改的密码。MDB 文件。

### <a name="setting-the-system-database"></a>设置系统数据库

下面是一个示例函数，用于设置将由应用程序使用的系统数据库。 在进行任何其他 DAO 调用之前，必须先调用此函数。

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

若要为系统数据库设置默认用户和密码，请使用以下函数：

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

更改的密码。MDB 文件，请使用以下函数：

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
