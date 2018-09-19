---
title: CAtlTransactionManager 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::Close
- ATLTRANSACTIONMANAGER/ATL::Commit
- ATLTRANSACTIONMANAGER/ATL::Create
- ATLTRANSACTIONMANAGER/ATL::CreateFile
- ATLTRANSACTIONMANAGER/ATL::DeleteFile
- ATLTRANSACTIONMANAGER/ATL::FindFirstFile
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributesEx
- ATLTRANSACTIONMANAGER/ATL::GetHandle
- ATLTRANSACTIONMANAGER/ATL::IsFallback
- ATLTRANSACTIONMANAGER/ATL::MoveFile
- ATLTRANSACTIONMANAGER/ATL::RegCreateKeyEx
- ATLTRANSACTIONMANAGER/ATL::RegDeleteKey
- ATLTRANSACTIONMANAGER/ATL::RegOpenKeyEx
- ATLTRANSACTIONMANAGER/ATL::Rollback
- ATLTRANSACTIONMANAGER/ATL::SetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::m_bFallback
- ATLTRANSACTIONMANAGER/ATL::m_hTransaction
dev_langs:
- C++
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6109ad46fb171d4bfe3386a4746b21768510ce0d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042438"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager 类

CAtlTransactionManager 类提供了对内核事务管理器 (KTM) 函数的包装器。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CAtlTransactionManager;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[~ CAtlTransactionManager](#dtor)|CAtlTransactionManager 析构函数。|
|[CAtlTransactionManager](#catltransactionmanager)|CAtlTransactionManager 构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[关闭](#close)|关闭其中一个事务句柄。|
|[提交](#commit)|该事务被提交的请求。|
|[创建](#create)|创建事务句柄。|
|[CreateFile](#createfile)|创建或打开文件、 文件流或事务处理操作的目录。|
|[DeleteFile](#deletefile)|作为事务处理操作中删除一个现有文件。|
|[FindFirstFile](#findfirstfile)|目录中搜索的文件或子目录作为事务处理操作。|
|[GetFileAttributes](#getfileattributes)|事务处理操作的形式检索指定的文件或目录的文件系统属性。|
|[GetFileAttributesEx](#getfileattributesex)|事务处理操作的形式检索指定的文件或目录的文件系统属性。|
|[GetHandle](#gethandle)|返回事务句柄。|
|[IsFallback](#isfallback)|确定是否启用回退的调用。|
|[MoveFile](#movefile)|将移动现有文件或目录，包括其子元素，作为事务处理操作。|
|[RegCreateKeyEx](#regcreatekeyex)|创建指定的注册表项并将其与事务关联。 如果该键已存在，该函数将打开它。|
|[RegDeleteKey](#regdeletekey)|作为事务处理操作，从注册表指定特定于平台的视图中删除子项和它的值。|
|[RegOpenKeyEx](#regopenkeyex)|打开指定的注册表项并将其与事务关联。|
|[回滚](#rollback)|事务被回滚的请求。|
|[SetFileAttributes](#setfileattributes)|将文件或目录的属性设置为事务处理操作。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|如果回退支持，则为 TRUEFALSE 否则为。|
|[m_hTransaction](#m_htransaction)|事务句柄。|

## <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

[ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>要求

**标头：** atltransactionmanager.h

##  <a name="dtor"></a>  ~ CAtlTransactionManager

CAtlTransactionManager 析构函数。

```
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>备注

在正常处理中，事务是自动提交并关闭。 如果异常展开期间调用的析构函数，是回滚事务并将其关闭。

##  <a name="catltransactionmanager"></a>  CAtlTransactionManager

CAtlTransactionManager 构造函数。

```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>参数

*bFallback*<br/>
TRUE 表示支持回退。 如果事务处理的函数失败，类会自动调用"非事务性"函数。 FALSE 表示未"回退"的调用。

*bAutoCreateTransaction*<br/>
TRUE 表示的构造函数中自动创建的事务处理程序。 FALSE 表示不是。

### <a name="remarks"></a>备注

##  <a name="close"></a>  关闭

关闭事务句柄。

```
inline BOOL Close();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用`CloseHandle`函数。 自动在析构函数中调用该方法。

##  <a name="commit"></a>  提交

该事务被提交的请求。

```
inline BOOL Commit();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用`CommitTransaction`函数。 自动在析构函数中调用该方法。

##  <a name="create"></a>  创建

创建事务句柄。

```
inline BOOL Create();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用`CreateTransaction`函数。 检查它的

##  <a name="createfile"></a>  CreateFile

创建或打开文件、 文件流或事务处理操作的目录。

```
inline HANDLE CreateFile(
    LPCTSTR lpFileName,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes,
    HANDLE hTemplateFile);
```

### <a name="parameters"></a>参数

*lpFileName*<br/>
若要创建或打开的对象的名称。

*dwDesiredAccess*<br/>
对可归纳如下读取、 写入、 两个，或都不 （零） 的对象的访问。 最常用的值有 GENERIC_READ、 generic_write 外，或两者： GENERIC_READ &#124; GENERIC_WRITE。

*dwShareMode*<br/>
一个对象，它可以是读取、 写入，同时，删除，所有这些操作，或无共享模式： 0，FILE_SHARE_DELETE，FILE_SHARE_READ，FILE_SHARE_WRITE。

*lpSecurityAttributes*<br/>
指向包含可选的安全描述符，并且还确定可以由子进程继承返回的句柄的 SECURITY_ATTRIBUTES 结构的指针。 参数可以为 NULL。

*dwCreationDisposition*<br/>
要在存在并且不存在的文件上执行的操作。 此参数必须是以下值，不能组合之一： CREATE_ALWAYS、 CREATE_NEW、 OPEN_ALWAYS、 OPEN_EXISTING 或 TRUNCATE_EXISTING。

*dwFlagsAndAttributes*<br/>
文件属性和标志。 此参数可以包括可用的文件属性 （FILE_ATTRIBUTE_ *） 的任意组合。 所有其他文件属性重写 FILE_ATTRIBUTE_NORMAL。 此参数还可以包含标志的组合 (FILE_FLAG_\*) 进行缓冲行为的控制，访问模式和其他专用的标志。 它们与任何 FILE_ATTRIBUTE_ 结合\*值。

*hTemplateFile*<br/>
有效句柄 GENERIC_READ 访问权限的模板文件。 模板文件提供文件属性和为其创建的文件的扩展的属性。 此参数可以为 NULL。

### <a name="return-value"></a>返回值

返回可用于访问对象的句柄。

### <a name="remarks"></a>备注

此包装器调用`CreateFileTransacted`函数。

##  <a name="deletefile"></a>  DeleteFile

作为事务处理操作中删除一个现有文件。

```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>参数

*lpFileName*<br/>
要删除的文件的名称。

### <a name="remarks"></a>备注

此包装器调用`DeleteFileTransacted`函数。

##  <a name="findfirstfile"></a>  FindFirstFile

目录中搜索的文件或子目录作为事务处理操作。

```
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>参数

*lpFileName*<br/>
目录或路径，以及要搜索的文件名称。 此参数可以包含通配符字符，如星号 （*） 或问号 （）。

*pNextInfo*<br/>
指向接收找到的文件或子目录的相关信息的 WIN32_FIND_DATA 结构的指针。

### <a name="return-value"></a>返回值

如果函数成功，返回值是对的后续调用中使用的搜索句柄`FindNextFile`或`FindClose`。 如果函数失败，或找不到文件中的搜索字符串*lpFileName*参数，则返回值为 INVALID_HANDLE_VALUE。

### <a name="remarks"></a>备注

此包装器调用`FindFirstFileTransacted`函数。

##  <a name="getfileattributes"></a>  GetFileAttributes

事务处理操作的形式检索指定的文件或目录的文件系统属性。

```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>参数

*lpFileName*<br/>
文件或目录的名称。

### <a name="remarks"></a>备注

此包装器调用`GetFileAttributesTransacted`函数。

##  <a name="getfileattributesex"></a>  GetFileAttributesEx

事务处理操作的形式检索指定的文件或目录的文件系统属性。

```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>参数

*lpFileName*<br/>
文件或目录的名称。

*fInfoLevelId*<br/>
要检索的属性信息的级别。

*lpFileInformation*<br/>
指向接收属性信息的缓冲区的指针。 存储到此缓冲区的属性信息的类型确定的值*fInfoLevelId*。 如果*fInfoLevelId*参数是 GetFileExInfoStandard，则此参数指向 WIN32_FILE_ATTRIBUTE_DATA 结构。

### <a name="remarks"></a>备注

此包装器调用`GetFileAttributesTransacted`函数。

##  <a name="gethandle"></a>  GetHandle

返回事务句柄。

```
HANDLE GetHandle() const;
```

### <a name="return-value"></a>返回值

返回一个类的事务句柄。 如果返回 NULL`CAtlTransactionManager`未附加到一个句柄。

### <a name="remarks"></a>备注

##  <a name="isfallback"></a>  IsFallback

确定是否启用回退的调用。

```
BOOL IsFallback() const;
```

### <a name="return-value"></a>返回值

类支持回退调用为返回 TRUE。 FALSE 否则为。

### <a name="remarks"></a>备注

##  <a name="m_bfallback"></a>  m_bFallback

如果回退支持，则为 TRUEFALSE 否则为。

```
BOOL m_bFallback;
```

### <a name="remarks"></a>备注

##  <a name="m_htransaction"></a>  m_hTransaction

事务句柄。

```
HANDLE m_hTransaction;
```

### <a name="remarks"></a>备注

##  <a name="movefile"></a>  MoveFile

将移动现有文件或目录，包括其子元素，作为事务处理操作。

```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>参数

*lpOldFileName*<br/>
当前的现有文件或本地计算机上的目录名称。

*lpNewFileName*<br/>
文件或目录的新名称。 此名称必须已存在。 一个新的文件可能位于不同的文件系统或驱动器。 新目录必须位于同一个驱动器上。

### <a name="remarks"></a>备注

此包装器调用`MoveFileTransacted`函数。

##  <a name="regcreatekeyex"></a>  RegCreateKeyEx

创建指定的注册表项并将其与事务关联。 如果该键已存在，该函数将打开它。

```
inline LSTATUS RegCreateKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD dwReserved,
    LPTSTR lpClass,
    DWORD dwOptions,
    REGSAM samDesired,
    CONST LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    PHKEY phkResult,
    LPDWORD lpdwDisposition);
```

### <a name="parameters"></a>参数

*hKey*<br/>
打开注册表项句柄。

*lpSubKey*<br/>
此函数将打开或创建一个子项的名称。

*dwReserved*<br/>
此参数保留并必须为零。

*lpClass*<br/>
此密钥的用户定义的类。 可能会忽略此参数。 此参数可以为 NULL。

*dwOptions*<br/>
此参数可以是下列值之一： REG_OPTION_BACKUP_RESTORE、 REG_OPTION_NON_VOLATILE 或 REG_OPTION_VOLATILE。

*samDesired*<br/>
一个屏蔽，它指定密钥的访问权限。

*lpSecurityAttributes*<br/>
指向 SECURITY_ATTRIBUTES 结构，用于确定返回的句柄能否由子进程继承。 如果*lpSecurityAttributes*为 NULL，不能继承句柄。

*phkResult*<br/>
指向一个变量来接收打开或创建密钥的句柄的指针。 如果键不是预定义的注册表项之一，则调用`RegCloseKey`函数使用句柄完成。

*lpdwDisposition*<br/>
指向一个变量来接收以下 disposition 值之一： REG_CREATED_NEW_KEY 或 REG_OPENED_EXISTING_KEY。

### <a name="return-value"></a>返回值

如果函数成功，返回值为 ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义一个非零错误代码。

### <a name="remarks"></a>备注

此包装器调用`RegCreateKeyTransacted`函数。

##  <a name="regdeletekey"></a>  RegDeleteKey

作为事务处理操作，从注册表指定特定于平台的视图中删除子项和它的值。

```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*hKey*|打开注册表项句柄。|
|*lpSubKey*|要删除的键的名称。|

### <a name="return-value"></a>返回值

如果函数成功，返回值为 ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义一个非零错误代码。

### <a name="remarks"></a>备注

此包装器调用`RegDeleteKeyTransacted`函数。

##  <a name="regopenkeyex"></a>  RegOpenKeyEx

打开指定的注册表项并将其与事务关联。

```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>参数

*hKey*<br/>
打开注册表项句柄。

*lpSubKey*<br/>
若要打开的注册表子项的名称。

*ulOptions*<br/>
此参数保留并必须为零。

*samDesired*<br/>
一个屏蔽，它指定密钥的访问权限。

*phkResult*<br/>
指向一个变量来接收打开或创建密钥的句柄的指针。 如果键不是预定义的注册表项之一，则调用`RegCloseKey`函数使用句柄完成。

### <a name="return-value"></a>返回值

如果函数成功，返回值为 ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义一个非零错误代码

### <a name="remarks"></a>备注

此包装器调用`RegOpenKeyTransacted`函数。

##  <a name="rollback"></a>  回滚

事务被回滚的请求。

```
inline BOOL Rollback();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用`RollbackTransaction`函数。

##  <a name="setfileattributes"></a>  SetFileAttributes

将文件或目录的属性设置为事务处理操作。

```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>参数

*lpFileName*<br/>
文件或目录的名称。

*dwAttributes*<br/>
若要为文件设置文件属性。 有关详细信息，请参阅[SetFileAttributesTransacted](/windows/desktop/api/winbase/nf-winbase-setfileattributestransacteda)。

### <a name="remarks"></a>备注

此包装器调用`SetFileAttributesTransacted`函数。

## <a name="see-also"></a>请参阅

[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)
