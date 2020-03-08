---
title: CGopherFileFind 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 55c40fc04934f00ccb541a01cce611d9532bee1a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875781"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind 类

辅助 Gopher 服务器的 Internet 文件搜索。

> [!NOTE]
>  类 `CGopherConnection`、`CGopherFile`、`CGopherFileFind`、`CGopherLocator` 及其成员已被弃用，因为它们不能在 Windows XP 平台上运行，但它们将继续在早期的平台上工作。

## <a name="syntax"></a>语法

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CGopherFileFind：： CGopherFileFind](#cgopherfilefind)|构造 `CGopherFileFind` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CGopherFileFind：： FindFile](#findfile)|在 gopher 服务器上查找文件。|
|[CGopherFileFind：： FindNextFile](#findnextfile)|继续对[FindFile](#findfile)进行的文件搜索。|
|[CGopherFileFind：： GetCreationTime](#getcreationtime)|获取指定文件的创建时间。|
|[CGopherFileFind：： GetLastAccessTime](#getlastaccesstime)|获取上次访问指定文件的时间。|
|[CGopherFileFind：： GetLastWriteTime](#getlastwritetime)|获取上次写入指定文件的时间。|
|[CGopherFileFind：： GetLength](#getlength)|获取找到的文件的长度（以字节为单位）。|
|[CGopherFileFind：： GetLocator](#getlocator)|获取 `CGopherLocator` 的对象。|
|[CGopherFileFind：： GetScreenName](#getscreenname)|获取 gopher 屏幕的名称。|
|[CGopherFileFind：： IsDots](#isdots)|测试当前目录和父目录标记，同时循环访问文件。|

## <a name="remarks"></a>备注

`CGopherFileFind` 包含开始搜索、查找文件和返回文件的 URL 的成员函数。

用于搜索 Internet 和本地文件的其他 MFC 类包括[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)和[CFileFind](../../mfc/reference/cfilefind-class.md)。 与 `CGopherFileFind`一起使用，这些类为用户提供了一种无缝机制来查找特定文件，而不考虑服务器协议、文件类型或位置（本地计算机或远程服务器）。请注意，没有用于在 HTTP 服务器上搜索的 MFC 类，因为 HTTP 不支持搜索所需的直接文件操作。

> [!NOTE]
> `CGopherFileFind` 不支持其基类[CFileFind](../../mfc/reference/cfilefind-class.md)的以下成员函数：

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

此外，当与 `CGopherFileFind`一起使用时，`CFileFind` 成员函数[IsDots](../../mfc/reference/cfilefind-class.md#isdots)始终为 FALSE。

有关如何使用 `CGopherFileFind` 和其他 WinInet 类的详细信息，请参阅文章[使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>要求

**标头：** afxinet。h

##  <a name="cgopherfilefind"></a>CGopherFileFind：： CGopherFileFind

调用此成员函数来构造 `CGopherFileFind` 的对象。

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*pConnection*<br/>
指向[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)对象的指针。

*dwContext*<br/>
操作的上下文标识符。 有关*dwContext*的详细信息，请参阅 "**备注**"。

### <a name="remarks"></a>备注

*DwContext*的默认值由 MFC 发送到创建 `CGopherFileFind` 对象的[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象中的 `CGopherFileFind` 对象。 构造 `CGopherFileFind` 对象时，可以重写默认值，将上下文标识符设置为所选的值。 上下文标识符返回到[CInternetSession：： OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) ，以在标识它的对象上提供状态。 有关上下文标识符的详细信息，请参阅文章[Internet 优先步骤： WinInet](../../mfc/wininet-basics.md) 。

##  <a name="findfile"></a>CGopherFileFind：： FindFile

调用此成员函数以查找 gopher 文件。

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
对[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象的引用。

*pstrString*<br/>
指向包含文件名的字符串的指针。

dwFlags<br/>
描述如何处理此会话的标志。 有效标志为：

- INTERNET_FLAG_RELOAD 从远程服务器获取数据，即使该数据在本地缓存也是如此。

- INTERNET_FLAG_DONT_CACHE 不会在本地或任何网关上缓存数据。

- INTERNET_FLAG_SECURE 通过安全套接字层或 PCT 请求连接到网络上的安全事务。 此标志仅适用于 HTTP 请求。

- INTERNET_FLAG_USE_EXISTING 如果可能，请为新的 `FindFile` 请求重用服务器的现有连接，而不是为每个请求创建新的会话。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 若要获得扩展的错误信息，请调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>备注

在调用 `FindFile` 检索第一个 gopher 对象后，可以调用[FindNextFile](#findnextfile)来检索后续的 gopher 文件。

##  <a name="findnextfile"></a>CGopherFileFind：： FindNextFile

调用此成员函数以继续对[CGopherFileFind：： FindFile](#findfile)的调用开始的文件搜索。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>返回值

如果有多个文件，则为非零值;如果找到的文件是目录中的最后一个，或者如果出现错误，则为零。 若要获得扩展的错误信息，请调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的文件是目录中的最后一个文件，或者找不到匹配的文件，则 `GetLastError` 函数将返回 ERROR_NO_MORE_FILES。

##  <a name="getcreationtime"></a>CGopherFileFind：： GetCreationTime

获取当前文件的创建时间。

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>参数

*pTimeStamp*<br/>
指向包含文件创建时间的[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构的指针。

*refTime*<br/>
对[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

### <a name="return-value"></a>返回值

如果成功，则为非零值;如果不成功，则为0。 仅当从未在此 `CGopherFileFind` 对象上调用[FindNextFile](#findnextfile)时，`GetCreationTime` 才返回0。

### <a name="remarks"></a>备注

调用 `GetCreationTime`之前，必须至少调用[FindNextFile](#findnextfile) 。

> [!NOTE]
>  并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性，则此函数返回的值可能与其他时间戳函数返回的值相同。 有关时间格式的信息，请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上，返回的时间是文件所在计算机的本地时区。 有关详细信息，请参阅 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

##  <a name="getlastaccesstime"></a>CGopherFileFind：： GetLastAccessTime

获取上次访问指定文件的时间。

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>参数

*refTime*<br/>
对[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

*pTimeStamp*<br/>
指向包含文件上次访问时间的[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则为非零值;如果不成功，则为0。 仅当从未在此 `CGopherFileFind` 对象上调用[FindNextFile](#findnextfile)时，`GetLastAccessTime` 才返回0。

### <a name="remarks"></a>备注

调用 `GetLastAccessTime`之前，必须至少调用[FindNextFile](#findnextfile) 。

> [!NOTE]
>  并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性，则此函数返回的值可能与其他时间戳函数返回的值相同。 有关时间格式的信息，请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上，返回的时间是文件所在计算机的本地时区。 有关详细信息，请参阅 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

##  <a name="getlastwritetime"></a>CGopherFileFind：： GetLastWriteTime

获取文件上次更改的时间。

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>参数

*pTimeStamp*<br/>
指向包含文件上次写入时间的[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构的指针。

*refTime*<br/>
对[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

### <a name="return-value"></a>返回值

如果成功，则为非零值;如果不成功，则为0。 仅当从未在此 `CGopherFileFind` 对象上调用[FindNextFile](#findnextfile)时，`GetLastWriteTime` 才返回0。

### <a name="remarks"></a>备注

调用 `GetLastWriteTime`之前，必须至少调用[FindNextFile](#findnextfile) 。

> [!NOTE]
>  并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性，则此函数返回的值可能与其他时间戳函数返回的值相同。 有关时间格式的信息，请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上，返回的时间是文件所在计算机的本地时区。 有关详细信息，请参阅 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

##  <a name="getlength"></a>CGopherFileFind：： GetLength

调用此成员函数以获取找到的文件的长度（以字节为单位）。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>返回值

找到的文件的长度（以字节为单位）。

### <a name="remarks"></a>备注

`GetLength` 使用 Win32 结构[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)获取文件大小的值（以字节为单位）。

> [!NOTE]
>  从 MFC 7.0，`GetLength` 支持64位整数类型。 以前-用此更新版本的库生成的现有代码可能会导致截断警告。

### <a name="example"></a>示例

  请参阅[CFile：： GetLength](../../mfc/reference/cfile-class.md#getlength) （基类实现）的示例。

##  <a name="getlocator"></a>CGopherFileFind：： GetLocator

调用此成员函数以获取[FindFile](#findfile)用于查找 gopher 文件的[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>返回值

一个 `CGopherLocator` 对象。

##  <a name="getscreenname"></a>CGopherFileFind：： GetScreenName

调用此成员函数以获取 gopher 屏幕的名称。

```
CString GetScreenName() const;
```

### <a name="return-value"></a>返回值

Gopher 屏幕的名称。

##  <a name="isdots"></a>CGopherFileFind：： IsDots

测试当前目录和父目录标记，同时循环访问文件。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>返回值

如果找到的文件的名称为 "." 或 ".."，则为非零值，表示找到的文件实际上是一个目录。 否则为0。

### <a name="remarks"></a>备注

调用 `IsDots`之前，必须至少调用[FindNextFile](#findnextfile) 。

## <a name="see-also"></a>另请参阅

[CFileFind 类](../../mfc/reference/cfilefind-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind 类](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind 类](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 类](../../mfc/reference/chttpfile-class.md)
