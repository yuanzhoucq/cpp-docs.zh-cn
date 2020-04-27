---
title: CAtlTransactionManager 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
ms.openlocfilehash: 968582feccd8ba9252ca009699eef6eae2c5c3d6
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167820"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager 类

CAtlTransactionManager 类提供内核事务管理器（KTM）函数的包装器。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```cpp
class CAtlTransactionManager;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[~ CAtlTransactionManager](#dtor)|CAtlTransactionManager 析构函数。|
|[CAtlTransactionManager](#catltransactionmanager)|CAtlTransactionManager 构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[关闭](#close)|关闭事务句柄。|
|[提交](#commit)|请求提交事务。|
|[创建](#create)|创建事务句柄。|
|[CreateFile](#createfile)|创建文件、文件流或目录作为事务处理操作。|
|[DeleteFile](#deletefile)|删除作为事务处理操作的现有文件。|
|[FindFirstFile](#findfirstfile)|在目录中搜索文件或子目录作为事务处理操作。|
|[GetFileAttributes](#getfileattributes)|检索指定文件或目录的文件系统属性作为事务处理操作。|
|[GetFileAttributesEx](#getfileattributesex)|检索指定文件或目录的文件系统属性作为事务处理操作。|
|[GetHandle](#gethandle)|返回事务句柄。|
|[IsFallback](#isfallback)|确定是否启用回退调用。|
|[MoveFile](#movefile)|将现有文件或目录（包括其子级）作为事务处理操作移动。|
|[RegCreateKeyEx](#regcreatekeyex)|创建指定的注册表项，并将其与事务关联。 如果该键已存在，则该函数将打开它。|
|[RegDeleteKey](#regdeletekey)|从指定的特定于平台的注册表视图中删除子项及其值作为事务处理操作。|
|[RegOpenKeyEx](#regopenkeyex)|打开指定的注册表项，并将其与事务关联。|
|[回退](#rollback)|请求回滚事务。|
|[SetFileAttributes](#setfileattributes)|将文件或目录的属性设置为事务处理操作。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|如果支持回退，则为 TRUE;否则为 FALSE。|
|[m_hTransaction](#m_htransaction)|事务句柄。|

## <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

[ATL：： CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>要求

**标头：** atltransactionmanager

## <a name="catltransactionmanager"></a><a name="dtor"></a>~ CAtlTransactionManager

CAtlTransactionManager 析构函数。

```cpp
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>备注

在正常处理过程中，将自动提交和关闭事务。 如果在异常展开期间调用了析构函数，则事务将回滚并关闭。

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a>CAtlTransactionManager

CAtlTransactionManager 构造函数。

```cpp
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>参数

*bFallback*<br/>
TRUE 表示支持回退。 如果事务处理函数失败，类将自动调用 "非事务性" 函数。 FALSE 表示没有 "回退" 调用。

*bAutoCreateTransaction*<br/>
TRUE 表示在构造函数中自动创建事务处理程序。 FALSE 指示它不是。

### <a name="remarks"></a>备注

## <a name="close"></a><a name="close"></a>封闭

关闭事务句柄。

```cpp
inline BOOL Close();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用`CloseHandle`函数。 方法自动在析构函数中调用。

## <a name="commit"></a><a name="commit"></a>立即

请求提交事务。

```cpp
inline BOOL Commit();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用`CommitTransaction`函数。 方法自动在析构函数中调用。

## <a name="create"></a><a name="create"></a>创建

创建事务句柄。

```cpp
inline BOOL Create();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用`CreateTransaction`函数。 检查

## <a name="createfile"></a><a name="createfile"></a>CreateFile

创建文件、文件流或目录作为事务处理操作。

```cpp
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
要创建或打开的对象的名称。

*dwDesiredAccess*<br/>
对对象的访问，可将其汇总为读取、写入和/或两者（零）。 最常使用的值 GENERIC_READ、GENERIC_WRITE 或二者都是 GENERIC_READ &#124; GENERIC_WRITE。

*dwShareMode*<br/>
对象的共享模式，可以是读取、写入、删除、删除、所有这些操作，也可以是 none：0，FILE_SHARE_DELETE，FILE_SHARE_READ，FILE_SHARE_WRITE。

*lpSecurityAttributes*<br/>
指向 SECURITY_ATTRIBUTES 结构的指针，该结构包含可选的安全描述符，还确定是否可以由子进程继承返回的句柄。 参数可以为 NULL。

*dwCreationDisposition*<br/>
对存在但不存在的文件执行的操作。 此参数必须是以下值之一，这些值不能是组合的： CREATE_ALWAYS、CREATE_NEW、OPEN_ALWAYS、OPEN_EXISTING 或 TRUNCATE_EXISTING。

*dwFlagsAndAttributes*<br/>
文件属性和标志。 此参数可以包含可用文件属性（FILE_ATTRIBUTE_ *）的任意组合。 所有其他文件特性都覆盖 FILE_ATTRIBUTE_NORMAL。 此参数还可以包含用于控制缓冲行为、\*访问模式和其他特殊用途标志的标志（FILE_FLAG_）组合。 这些值与任何 FILE_ATTRIBUTE_\*值组合在一起。

*hTemplateFile*<br/>
具有 GENERIC_READ 访问权限的模板文件的有效句柄。 模板文件提供要创建的文件的文件属性和扩展属性。 此参数可以为 NULL。

### <a name="return-value"></a>返回值

返回可用于访问对象的句柄。

### <a name="remarks"></a>备注

此包装器调用`CreateFileTransacted`函数。

## <a name="deletefile"></a><a name="deletefile"></a>DeleteFile

删除作为事务处理操作的现有文件。

```cpp
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>参数

*lpFileName*<br/>
要删除的文件的名称。

### <a name="remarks"></a>备注

此包装器调用`DeleteFileTransacted`函数。

## <a name="findfirstfile"></a><a name="findfirstfile"></a>FindFirstFile

在目录中搜索文件或子目录作为事务处理操作。

```cpp
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>参数

*lpFileName*<br/>
要搜索的目录或路径以及文件名。 此参数可以包含通配符，如星号（*）或问号（）。

*pNextInfo*<br/>
指向 WIN32_FIND_DATA 结构的指针，该结构接收找到的文件或子目录的相关信息。

### <a name="return-value"></a>返回值

如果该函数成功，则返回值是在对`FindNextFile`或`FindClose`的后续调用中使用的搜索句柄。 如果函数在*lpFileName*参数中的搜索字符串中未能找到文件，则返回值为 INVALID_HANDLE_VALUE。

### <a name="remarks"></a>备注

此包装器调用`FindFirstFileTransacted`函数。

## <a name="getfileattributes"></a><a name="getfileattributes"></a>GetFileAttributes

检索指定文件或目录的文件系统属性作为事务处理操作。

```cpp
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>参数

*lpFileName*<br/>
文件或目录的名称。

### <a name="remarks"></a>备注

此包装器调用`GetFileAttributesTransacted`函数。

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a>GetFileAttributesEx

检索指定文件或目录的文件系统属性作为事务处理操作。

```cpp
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
指向接收属性信息的缓冲区的指针。 存储在此缓冲区中的属性信息的类型由*fInfoLevelId*的值确定。 如果*fInfoLevelId*参数为 GetFileExInfoStandard，则此参数指向 WIN32_FILE_ATTRIBUTE_DATA 结构。

### <a name="remarks"></a>备注

此包装器调用`GetFileAttributesTransacted`函数。

## <a name="gethandle"></a><a name="gethandle"></a>GetHandle

返回事务句柄。

```cpp
HANDLE GetHandle() const;
```

### <a name="return-value"></a>返回值

返回类的事务句柄。 如果`CAtlTransactionManager`未附加到句柄，则返回 NULL。

### <a name="remarks"></a>备注

## <a name="isfallback"></a><a name="isfallback"></a>IsFallback

确定是否启用回退调用。

```cpp
BOOL IsFallback() const;
```

### <a name="return-value"></a>返回值

如果类支持回退调用，则返回 TRUE。 否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="m_bfallback"></a><a name="m_bfallback"></a>m_bFallback

如果支持回退，则为 TRUE;否则为 FALSE。

```cpp
BOOL m_bFallback;
```

### <a name="remarks"></a>备注

## <a name="m_htransaction"></a><a name="m_htransaction"></a>m_hTransaction

事务句柄。

```cpp
HANDLE m_hTransaction;
```

### <a name="remarks"></a>备注

## <a name="movefile"></a><a name="movefile"></a>MoveFile

将现有文件或目录（包括其子级）作为事务处理操作移动。

```cpp
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>参数

*lpOldFileName*<br/>
本地计算机上现有文件或目录的当前名称。

*lpNewFileName*<br/>
文件或目录的新名称。 此名称不能已存在。 新文件可能位于不同的文件系统或驱动器上。 新目录必须位于同一驱动器上。

### <a name="remarks"></a>备注

此包装器调用`MoveFileTransacted`函数。

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a>RegCreateKeyEx

创建指定的注册表项，并将其与事务关联。 如果该键已存在，则该函数将打开它。

```cpp
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
打开的注册表项的句柄。

*lpSubKey*<br/>
此函数打开或创建的子项的名称。

*dwReserved*<br/>
此参数为保留参数，必须为零。

*lpClass*<br/>
此键的用户定义类。 此参数可能会被忽略。 此参数可以为 NULL。

*dwOptions*<br/>
此参数可以是下列值之一： REG_OPTION_BACKUP_RESTORE、REG_OPTION_NON_VOLATILE 或 REG_OPTION_VOLATILE。

*samDesired*<br/>
指定密钥的访问权限的掩码。

*lpSecurityAttributes*<br/>
指向 SECURITY_ATTRIBUTES 结构的指针，此结构确定返回的句柄是否由子进程继承。 如果*lpSecurityAttributes*为 NULL，则不能继承句柄。

*phkResult*<br/>
指向一个变量的指针，该变量接收已打开或已创建的键的句柄。 如果该密钥不是预定义的注册表项之一，请在`RegCloseKey`使用完该句柄后调用该函数。

*lpdwDisposition*<br/>
指向一个变量的指针，该变量接收以下某个处置值： REG_CREATED_NEW_KEY 或 REG_OPENED_EXISTING_KEY。

### <a name="return-value"></a>返回值

如果该函数成功，则返回值为 ERROR_SUCCESS。 如果函数失败，则返回值为 Winerror.h 中定义的非零错误代码。

### <a name="remarks"></a>备注

此包装器调用`RegCreateKeyTransacted`函数。

## <a name="regdeletekey"></a><a name="regdeletekey"></a>RegDeleteKey

从指定的特定于平台的注册表视图中删除子项及其值作为事务处理操作。

```cpp
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*hKey*|打开的注册表项的句柄。|
|*lpSubKey*|要删除的密钥的名称。|

### <a name="return-value"></a>返回值

如果该函数成功，则返回值为 ERROR_SUCCESS。 如果函数失败，则返回值为 Winerror.h 中定义的非零错误代码。

### <a name="remarks"></a>备注

此包装器调用`RegDeleteKeyTransacted`函数。

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a>RegOpenKeyEx

打开指定的注册表项，并将其与事务关联。

```cpp
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>参数

*hKey*<br/>
打开的注册表项的句柄。

*lpSubKey*<br/>
要打开的注册表子项的名称。

*ulOptions*<br/>
此参数为保留参数，必须为零。

*samDesired*<br/>
指定密钥的访问权限的掩码。

*phkResult*<br/>
指向一个变量的指针，该变量接收已打开或已创建的键的句柄。 如果该密钥不是预定义的注册表项之一，请在`RegCloseKey`使用完该句柄后调用该函数。

### <a name="return-value"></a>返回值

如果该函数成功，则返回值为 ERROR_SUCCESS。 如果函数失败，则返回值为 Winerror.h 中定义的非零错误代码

### <a name="remarks"></a>备注

此包装器调用`RegOpenKeyTransacted`函数。

## <a name="rollback"></a><a name="rollback"></a>回退

请求回滚事务。

```cpp
inline BOOL Rollback();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用`RollbackTransaction`函数。

## <a name="setfileattributes"></a><a name="setfileattributes"></a>SetFileAttributes

将文件或目录的属性设置为事务处理操作。

```cpp
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>参数

*lpFileName*<br/>
文件或目录的名称。

*dwAttributes*<br/>
要为文件设置的文件特性。 有关详细信息，请参阅[SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw)。

### <a name="remarks"></a>备注

此包装器调用`SetFileAttributesTransacted`函数。

## <a name="see-also"></a>另请参阅

[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)
