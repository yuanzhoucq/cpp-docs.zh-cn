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
ms.openlocfilehash: 5c2814f963ea4814e0d7585e0e4d6dda26c1f04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321327"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager 类

CAtl交易管理器类提供内核事务管理器 （KTM） 函数的包装。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CAtlTransactionManager;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[*交易管理器](#dtor)|CAtl交易管理器析构函数。|
|[CAtl 交易管理器](#catltransactionmanager)|CAtl交易管理器构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[关闭](#close)|关闭事务句柄的一个。|
|[提交](#commit)|请求提交事务。|
|[创建](#create)|创建事务句柄。|
|[CreateFile](#createfile)|创建或打开文件、文件流或目录作为事务操作。|
|[DeleteFile](#deletefile)|将现有文件删除为事务操作。|
|[查找第一文件](#findfirstfile)|将文件或子目录搜索为已处理的操作。|
|[获取文件属性](#getfileattributes)|检索指定文件或目录的文件系统属性作为事务操作。|
|[获取文件属性Ex](#getfileattributesex)|检索指定文件或目录的文件系统属性作为事务操作。|
|[获取手柄](#gethandle)|返回事务句柄。|
|[是倒退](#isfallback)|确定是否启用回退调用。|
|[MoveFile](#movefile)|将现有文件或目录（包括其子文件）作为事务操作移动。|
|[注册创造键Ex](#regcreatekeyex)|创建指定的注册表项并将其与事务关联。 如果密钥已存在，则函数将打开它。|
|[注册删除键](#regdeletekey)|从注册表的指定平台特定视图中删除子键及其值，作为事务操作。|
|[RegOpenKeyEx](#regopenkeyex)|打开指定的注册表项并将其与事务关联。|
|[回 滚](#rollback)|请求回滚事务。|
|[设置文件属性](#setfileattributes)|将文件或目录的属性设置为事务处理操作。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|如果支持回退，则为 TRUE;否则。|
|[m_hTransaction](#m_htransaction)|事务句柄。|

## <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

[ATL：：CAtl交易管理器](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>要求

**标题：** atl交易管理器.h

## <a name="catltransactionmanager"></a><a name="dtor"></a>*交易管理器

CAtl交易管理器析构函数。

```
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>备注

在正常处理中，事务将自动提交并关闭。 如果在异常展开期间调用析构函数，则事务将回滚并关闭。

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a>CAtl 交易管理器

CAtl交易管理器构造函数。

```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>参数

*b 回退*<br/>
TRUE 表示支持回退。 如果事务处理的函数失败，类将自动调用"非事务化"函数。 FALSE 表示没有"回退"呼叫。

*b自动创建交易*<br/>
TRUE 表示事务处理程序是在构造函数中自动创建的。 FALSE 表示它不是。

### <a name="remarks"></a>备注

## <a name="close"></a><a name="close"></a>关闭

关闭事务句柄。

```
inline BOOL Close();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用函数`CloseHandle`。 该方法在析构函数中自动调用。

## <a name="commit"></a><a name="commit"></a>提交

请求提交事务。

```
inline BOOL Commit();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用函数`CommitTransaction`。 该方法在析构函数中自动调用。

## <a name="create"></a><a name="create"></a>创建

创建事务句柄。

```
inline BOOL Create();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用函数`CreateTransaction`。 检查其

## <a name="createfile"></a><a name="createfile"></a>创建文件

创建或打开文件、文件流或目录作为事务操作。

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

*lpFile名称*<br/>
要创建或打开的对象的名称。

*dwddAccess*<br/>
对对象的访问，可以概括为读取、写入，两者，或两者（零）。 最常用的值是GENERIC_READ、GENERIC_WRITE 或两者：GENERIC_READ&#124;GENERIC_WRITE。

*dwShareMode*<br/>
对象的共享模式，可以读取、写入、删除所有这些内容，或者无：0、FILE_SHARE_DELETE、FILE_SHARE_READFILE_SHARE_WRITE。

*lp安全属性*<br/>
指向SECURITY_ATTRIBUTES结构的指针，其中包含可选的安全描述符，并确定返回的句柄是否可以由子进程继承。 参数可以是 NULL。

*德沃创意*<br/>
要对存在和不存在的文件执行的操作。 此参数必须是无法组合的以下值之一：CREATE_ALWAYS、CREATE_NEW、OPEN_ALWAYS、OPEN_EXISTING或TRUNCATE_EXISTING。

*dwflags 和属性*<br/>
文件属性和标志。 此参数可以包括可用文件属性 （FILE_ATTRIBUTE_* 的任意组合。 所有其他文件属性都覆盖FILE_ATTRIBUTE_NORMAL。 此参数还可以包含用于控制缓冲行为、访问\*模式和其他特殊用途标志的标志 （FILE_FLAG_ ） 的组合。 这些值与任何FILE_ATTRIBUTE_\*值结合使用。

*h模板文件*<br/>
具有GENERIC_READ访问权限的模板文件的有效句柄。 模板文件为正在创建的文件提供文件属性和扩展属性。 此参数可以是 NULL。

### <a name="return-value"></a>返回值

返回可用于访问对象的句柄。

### <a name="remarks"></a>备注

此包装器调用函数`CreateFileTransacted`。

## <a name="deletefile"></a><a name="deletefile"></a>删除文件

将现有文件删除为事务操作。

```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>参数

*lpFile名称*<br/>
要删除的文件的名称。

### <a name="remarks"></a>备注

此包装器调用函数`DeleteFileTransacted`。

## <a name="findfirstfile"></a><a name="findfirstfile"></a>查找第一文件

将文件或子目录搜索为已处理的操作。

```
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>参数

*lpFile名称*<br/>
要搜索的目录或路径以及文件名。 此参数可以包括通配符，如星号 （*） 或问号 （）。

*pNext信息*<br/>
指向WIN32_FIND_DATA结构的指针，该结构接收有关找到的文件或子目录的信息。

### <a name="return-value"></a>返回值

如果函数成功，则返回值是后续调用`FindNextFile`或`FindClose`中使用的搜索句柄。 如果函数失败或无法从*lpFileName*参数中的搜索字符串中查找文件，则返回值INVALID_HANDLE_VALUE。

### <a name="remarks"></a>备注

此包装器调用函数`FindFirstFileTransacted`。

## <a name="getfileattributes"></a><a name="getfileattributes"></a>获取文件属性

检索指定文件或目录的文件系统属性作为事务操作。

```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>参数

*lpFile名称*<br/>
文件或目录的名称。

### <a name="remarks"></a>备注

此包装器调用函数`GetFileAttributesTransacted`。

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a>获取文件属性Ex

检索指定文件或目录的文件系统属性作为事务操作。

```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>参数

*lpFile名称*<br/>
文件或目录的名称。

*fInfoLevelId*<br/>
要检索的属性信息级别。

*lpFile信息*<br/>
指向接收属性信息的缓冲区的指针。 存储在此缓冲区中的属性信息的类型由*fInfoLevelId*的值决定。 如果*fInfoLevelId*参数为 GetFileExInfoStandard，则此参数指向WIN32_FILE_ATTRIBUTE_DATA结构。

### <a name="remarks"></a>备注

此包装器调用函数`GetFileAttributesTransacted`。

## <a name="gethandle"></a><a name="gethandle"></a>获取手柄

返回事务句柄。

```
HANDLE GetHandle() const;
```

### <a name="return-value"></a>返回值

返回类的事务句柄。 如果 未附加到`CAtlTransactionManager`句柄，则返回 NULL。

### <a name="remarks"></a>备注

## <a name="isfallback"></a><a name="isfallback"></a>是倒退

确定是否启用回退调用。

```
BOOL IsFallback() const;
```

### <a name="return-value"></a>返回值

返回 TRUE 是类支持回退调用。 否则。

### <a name="remarks"></a>备注

## <a name="m_bfallback"></a><a name="m_bfallback"></a>m_bFallback

如果支持回退，则为 TRUE;否则。

```
BOOL m_bFallback;
```

### <a name="remarks"></a>备注

## <a name="m_htransaction"></a><a name="m_htransaction"></a>m_hTransaction

事务句柄。

```
HANDLE m_hTransaction;
```

### <a name="remarks"></a>备注

## <a name="movefile"></a><a name="movefile"></a>移动文件

将现有文件或目录（包括其子文件）作为事务操作移动。

```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>参数

*lpOld文件名称*<br/>
本地计算机上的现有文件或目录的当前名称。

*lpNewFile名称*<br/>
文件或目录的新名称。 此名称必须不存在。 新文件可能位于其他文件系统或驱动器上。 新目录必须位于同一驱动器上。

### <a name="remarks"></a>备注

此包装器调用函数`MoveFileTransacted`。

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a>注册创造键Ex

创建指定的注册表项并将其与事务关联。 如果密钥已存在，则函数将打开它。

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

*h键*<br/>
打开注册表项的句柄。

*lpSubkey*<br/>
此函数打开或创建的子键的名称。

*dw保留*<br/>
此参数已保留，必须为零。

*lpClass*<br/>
此键的用户定义类。 可以忽略此参数。 此参数可以是 NULL。

*dwOptions*<br/>
此参数可以是以下值之一：REG_OPTION_BACKUP_RESTORE、REG_OPTION_NON_VOLATILE 或REG_OPTION_VOLATILE。

*萨姆·阿乔*<br/>
指定密钥的访问权限的掩码。

*lp安全属性*<br/>
指向 SECURITY_ATTRIBUTES 结构的指针，此结构确定返回的句柄是否由子进程继承。 如果*lpSecurity 属性*为 NULL，则无法继承该句柄。

*phkResult*<br/>
指向接收打开或创建的键的句柄的变量的指针。 如果密钥不是预定义的注册表项之一，则在使用完句柄`RegCloseKey`后调用该函数。

*lpdw 处理*<br/>
指向接收以下处置值之一的变量的指针：REG_CREATED_NEW_KEY或REG_OPENED_EXISTING_KEY。

### <a name="return-value"></a>返回值

如果函数成功，则返回值ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义的非零错误代码。

### <a name="remarks"></a>备注

此包装器调用函数`RegCreateKeyTransacted`。

## <a name="regdeletekey"></a><a name="regdeletekey"></a>注册删除键

从注册表的指定平台特定视图中删除子键及其值，作为事务操作。

```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*h键*|打开注册表项的句柄。|
|*lpSubkey*|要删除的键的名称。|

### <a name="return-value"></a>返回值

如果函数成功，则返回值ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义的非零错误代码。

### <a name="remarks"></a>备注

此包装器调用函数`RegDeleteKeyTransacted`。

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a>RegOpenKeyEx

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

*h键*<br/>
打开注册表项的句柄。

*lpSubkey*<br/>
要打开的注册表子键的名称。

*ulOptions*<br/>
此参数已保留，必须为零。

*萨姆·阿乔*<br/>
指定密钥的访问权限的掩码。

*phkResult*<br/>
指向接收打开或创建的键的句柄的变量的指针。 如果密钥不是预定义的注册表项之一，则在使用完句柄`RegCloseKey`后调用该函数。

### <a name="return-value"></a>返回值

如果函数成功，则返回值ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义的非零错误代码。

### <a name="remarks"></a>备注

此包装器调用函数`RegOpenKeyTransacted`。

## <a name="rollback"></a><a name="rollback"></a>回 滚

请求回滚事务。

```
inline BOOL Rollback();
```

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

此包装器调用函数`RollbackTransaction`。

## <a name="setfileattributes"></a><a name="setfileattributes"></a>设置文件属性

将文件或目录的属性设置为事务处理操作。

```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>参数

*lpFile名称*<br/>
文件或目录的名称。

*dwAttributes*<br/>
要为文件设置的文件属性。 有关详细信息，请参阅[设置文件属性转换](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw)。

### <a name="remarks"></a>备注

此包装器调用函数`SetFileAttributesTransacted`。

## <a name="see-also"></a>另请参阅

[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)
