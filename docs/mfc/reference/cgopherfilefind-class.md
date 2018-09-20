---
title: CGopherFileFind 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
dev_langs:
- C++
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a66ba34356fbc429421f1e9e9e547e7392220a8a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374474"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind 类

辅助 Gopher 服务器的 Internet 文件搜索。

> [!NOTE]
>  类`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和它们的成员具有已弃用，因为它们不能在 Windows XP 平台上，但它们将继续在早期版本的平台上工作。

## <a name="syntax"></a>语法

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|构造 `CGopherFileFind` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CGopherFileFind::FindFile](#findfile)|查找 gopher 服务器上的文件。|
|[CGopherFileFind::FindNextFile](#findnextfile)|将继续通过以前调用文件搜索[FindFile](#findfile)。|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|获取指定的文件的创建的时间。|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|获取上次访问指定的文件的时间。|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|获取上次写入指定的文件的时间。|
|[CGopherFileFind::GetLength](#getlength)|获取找到的文件，以字节为单位的长度。|
|[CGopherFileFind::GetLocator](#getlocator)|获取`CGopherLocator`对象。|
|[CGopherFileFind::GetScreenName](#getscreenname)|获取 gopher 屏幕的名称。|
|[CGopherFileFind::IsDots](#isdots)|循环访问文件时的当前目录和父目录标记的测试。|

## <a name="remarks"></a>备注

`CGopherFileFind` 包含成员函数来开始搜索，找到文件，并返回文件的 URL。

此演示适合对于 Internet 和本地文件搜索包括其他 MFC 类[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)并[CFileFind](../../mfc/reference/cfilefind-class.md)。 连同`CGopherFileFind`，这些类提供无缝的机制，用户可以查找特定文件，而不考虑服务器协议、 文件类型或位置 （本地计算机或远程服务器。）请注意，搜索 HTTP 服务器上，因为 HTTP 不支持直接进行文件操作所需的搜索没有 MFC 类。

> [!NOTE]
> `CGopherFileFind` 不支持其基本类的以下成员函数[CFileFind](../../mfc/reference/cfilefind-class.md):

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

此外，与一起使用时`CGopherFileFind`，则`CFileFind`成员函数[IsDots](../../mfc/reference/cfilefind-class.md#isdots)始终为 FALSE。

有关如何使用详细信息`CGopherFileFind`和其他 WinInet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>要求

**标头：** afxinet.h

##  <a name="cgopherfilefind"></a>  CGopherFileFind::CGopherFileFind

调用此成员函数来构造`CGopherFileFind`对象。

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*pConnection*<br/>
一个指向[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)对象。

*dwContext*<br/>
操作的上下文标识符。 请参阅**备注**有关详细信息*dwContext*。

### <a name="remarks"></a>备注

默认值为*dwContext*发送到 mfc`CGopherFileFind`对象从[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建`CGopherFileFind`对象。 构造时`CGopherFileFind`对象，您可以覆盖默认值为所选的值设置上下文标识符。 上下文标识符就会归还[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供与该标识的对象上的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。

##  <a name="findfile"></a>  CGopherFileFind::FindFile

调用此成员函数以找到 gopher 文件。

```
virtual BOOL FindFile(
    CGopherLocator& refLocator,
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);


virtual BOOL FindFile(
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>参数

*refLocator*<br/>
对引用[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。

*pstrString*<br/>
指向包含文件名称的字符串的指针。

*dwFlags*<br/>
描述如何处理此会话标志。 是有效的标志：

- 即使本地缓存，INTERNET_FLAG_RELOAD 从远程服务器获取数据。

- INTERNET_FLAG_DONT_CACHE 不缓存数据，本地或在任何网关。

- 使用安全套接字层或百分比在网络上 INTERNET_FLAG_SECURE 请求安全事务 此标志为适用于仅 HTTP 请求。

- INTERNET_FLAG_USE_EXISTING 如果可能，请重复使用现有连接到服务器的新`FindFile`请求，而不是创建新的会话的每个请求。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 若要获得扩展错误信息，请调用 Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

### <a name="remarks"></a>备注

在调用`FindFile`若要检索的第一个 gopher 对象，可以调用[FindNextFile](#findnextfile)检索后续 gopher 文件。

##  <a name="findnextfile"></a>  CGopherFileFind::FindNextFile

调用此成员函数以继续文件搜索开始通过调用[CGopherFileFind::FindFile](#findfile)。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>返回值

非零，如果有多个文件;如果找到该文件是在目录中的最后一个，或如果出错，则为零。 若要获得扩展错误信息，请调用 Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)。 如果找到该文件是在目录中的最后一个文件，或者如果没有匹配的可以找到文件，`GetLastError`函数返回 ERROR_NO_MORE_FILES。

##  <a name="getcreationtime"></a>  CGopherFileFind::GetCreationTime

获取当前文件的创建时间。

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>参数

*pTimeStamp*<br/>
一个指向[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284)结构，它包含该文件的创建的时间。

*refTime*<br/>
对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。

### <a name="return-value"></a>返回值

如果成功，则非零值如果不成功，则为 0。 `GetCreationTime` 仅当返回 0 [FindNextFile](#findnextfile)永远不会对此已调用`CGopherFileFind`对象。

### <a name="remarks"></a>备注

必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetCreationTime`。

> [!NOTE]
>  不是所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可返回相同的基础文件系统或服务器不支持保留的时间属性时，返回的其他时间戳函数的值。 请参阅[Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)结构有关的时间格式的信息。 在某些操作系统上返回的时间是在区域本地计算机到了该文件的所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) API 的详细信息。

##  <a name="getlastaccesstime"></a>  CGopherFileFind::GetLastAccessTime

获取上次访问指定的文件的时间。

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>参数

*refTime*<br/>
对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。

*pTimeStamp*<br/>
一个指向[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284)结构，它包含上一次访问该文件的时间。

### <a name="return-value"></a>返回值

如果成功，则非零值如果不成功，则为 0。 `GetLastAccessTime` 仅当返回 0 [FindNextFile](#findnextfile)永远不会对此已调用`CGopherFileFind`对象。

### <a name="remarks"></a>备注

必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetLastAccessTime`。

> [!NOTE]
>  不是所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可返回相同的基础文件系统或服务器不支持保留的时间属性时，返回的其他时间戳函数的值。 请参阅[Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)结构有关的时间格式的信息。 在某些操作系统上返回的时间是在区域本地计算机到了该文件的所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) API 的详细信息。

##  <a name="getlastwritetime"></a>  CGopherFileFind::GetLastWriteTime

获取已更改的文件的最后一个时间。

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>参数

*pTimeStamp*<br/>
一个指向[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284)结构，其中包含上次写入文件的时间。

*refTime*<br/>
对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。

### <a name="return-value"></a>返回值

如果成功，则非零值如果不成功，则为 0。 `GetLastWriteTime` 仅当返回 0 [FindNextFile](#findnextfile)永远不会对此已调用`CGopherFileFind`对象。

### <a name="remarks"></a>备注

必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetLastWriteTime`。

> [!NOTE]
>  不是所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可返回相同的基础文件系统或服务器不支持保留的时间属性时，返回的其他时间戳函数的值。 请参阅[Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)结构有关的时间格式的信息。 在某些操作系统上返回的时间是在区域本地计算机到了该文件的所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) API 的详细信息。

##  <a name="getlength"></a>  CGopherFileFind::GetLength

调用此成员函数要获取长度，以字节为单位的找到的文件。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>返回值

找到的文件长度 （字节）。

### <a name="remarks"></a>备注

`GetLength` 使用 Win32 结构[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)若要获取的文件大小的值以字节为单位。

> [!NOTE]
>  截至 MFC 7.0`GetLength`支持 64 位整数类型。 使用此较新版本的库生成的之前存在的代码可能会导致截断警告。

### <a name="example"></a>示例

  有关示例，请参阅[CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) （基类实现）。

##  <a name="getlocator"></a>  CGopherFileFind::GetLocator

调用此成员函数可获取[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象的[FindFile](#findfile)使用查找 gopher 文件。

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>返回值

一个 `CGopherLocator` 对象。

##  <a name="getscreenname"></a>  CGopherFileFind::GetScreenName

调用此成员函数可获取 gopher 屏幕的名称。

```
CString GetScreenName() const;
```

### <a name="return-value"></a>返回值

Gopher 屏幕的名称。

##  <a name="isdots"></a>  CGopherFileFind::IsDots

循环访问文件时的当前目录和父目录标记的测试。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>返回值

如果找到的文件具有的名称，非零值"。".."，指示找到的文件是一个目录。 否则为 0。

### <a name="remarks"></a>备注

必须调用[FindNextFile](#findnextfile)至少一次之前调用`IsDots`。

## <a name="see-also"></a>请参阅

[CFileFind 类](../../mfc/reference/cfilefind-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind 类](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind 类](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 类](../../mfc/reference/chttpfile-class.md)
