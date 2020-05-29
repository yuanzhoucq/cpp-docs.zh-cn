---
title: CGopher文件查找类
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
ms.openlocfilehash: 7a42b99c919abd9098bff1897c4c5febf443314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373680"
---
# <a name="cgopherfilefind-class"></a>CGopher文件查找类

辅助 Gopher 服务器的 Internet 文件搜索。

> [!NOTE]
> 类`CGopherConnection` `CGopherFile`、 `CGopherFileFind`、`CGopherLocator`及其成员已被弃用，因为它们在 Windows XP 平台上不工作，但它们将继续在较早的平台上工作。

## <a name="syntax"></a>语法

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CGopher文件查找：：CGopher文件查找](#cgopherfilefind)|构造 `CGopherFileFind` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CGopher文件查找：查找文件](#findfile)|在 gopher 服务器上查找文件。|
|[CGopher文件查找：：查找下一个文件](#findnextfile)|继续从上一个调用[FindFile](#findfile)的文件搜索。|
|[CGopher文件查找：获取创造时间](#getcreationtime)|获取创建指定文件的时间。|
|[CGopher文件查找：获取最后访问时间](#getlastaccesstime)|获取上次访问指定文件的时间。|
|[CGopher文件查找：获取最后写入时间](#getlastwritetime)|获取上次写入指定文件的时间。|
|[CGopher文件查找：获取长度](#getlength)|获取找到文件的长度（以字节为单位）。|
|[CGopher文件查找：获取定位器](#getlocator)|获取`CGopherLocator`对象。|
|[CGopher文件查找：获取屏幕名称](#getscreenname)|获取高时屏幕的名称。|
|[CGopher文件查找：：是点](#isdots)|测试当前目录和父目录标记，同时遍历文件。|

## <a name="remarks"></a>备注

`CGopherFileFind`包括开始搜索、查找文件并返回文件 URL 的成员函数。

其他为互联网和本地文件搜索设计的MFC类包括[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)和[CFileFind。](../../mfc/reference/cfilefind-class.md) 与`CGopherFileFind`配合这些类为用户提供了一个无缝机制，以便用户查找特定文件，而不管服务器协议、文件类型或位置（本地计算机或远程服务器）。请注意，没有用于在 HTTP 服务器上搜索的 MFC 类，因为 HTTP 不支持搜索所需的直接文件操作。

> [!NOTE]
> `CGopherFileFind`不支持其基类[CFileFind](../../mfc/reference/cfilefind-class.md)的以下成员函数：

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [获取文件路径](../../mfc/reference/cfilefind-class.md#getfilepath)

- [获取文件标题](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [获取文件URL](../../mfc/reference/cfilefind-class.md#getfileurl)

此外，当与`CGopherFileFind`使用 时`CFileFind`，成员函数[IsDots](../../mfc/reference/cfilefind-class.md#isdots)始终为 FALSE。

有关如何使用`CGopherFileFind`和其他 WinInet 类的详细信息，请参阅[使用 WinInet 进行 Internet 编程的文章](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="cgopherfilefindcgopherfilefind"></a><a name="cgopherfilefind"></a>CGopher文件查找：：CGopher文件查找

调用此成员函数以构造对象`CGopherFileFind`。

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*p连接*<br/>
指向[Gopher 连接](../../mfc/reference/cgopherconnection-class.md)对象的指针。

*dwContext*<br/>
操作的上下文标识符。 有关*dwContext*的详细信息，请参阅**备注**。

### <a name="remarks"></a>备注

mFC 从`CGopherFileFind`创建对象的[CInternetSession](../../mfc/reference/cinternetsession-class.md) `CGopherFileFind`对象向对象发送*dwContext*的默认值。 构造`CGopherFileFind`对象时，可以重写默认值，将上下文标识符设置为您选择的值。 上下文标识符返回到[CInternetSession：：onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供标识它的对象的状态。 有关上下文标识符的详细信息[，请参阅"Internet 第一步：WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="cgopherfilefindfindfile"></a><a name="findfile"></a>CGopher文件查找：查找文件

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

*参考定位器*<br/>
对[CGopher 定位器对象的引用](../../mfc/reference/cgopherlocator-class.md)。

*普斯特林*<br/>
指向包含文件名的字符串的指针。

dwFlags**<br/>
描述如何处理此会话的标志。 有效标志包括：

- INTERNET_FLAG_RELOAD 从远程服务器获取数据，即使它是本地缓存的。

- INTERNET_FLAG_DONT_CACHE不要在本地或任何网关中缓存数据。

- INTERNET_FLAG_SECURE使用安全套接字层或PCT请求线上的安全交易。 此标志仅适用于 HTTP 请求。

- INTERNET_FLAG_USE_EXISTING 如果可能，请重用与服务器的现有连接以访问`FindFile`新请求，而不是为每个请求创建新会话。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 要获取扩展错误信息，请致电 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>备注

调用`FindFile`以检索第一个 gopher 对象后，可以调用[FindNextFile](#findnextfile)来检索后续的 gopher 文件。

## <a name="cgopherfilefindfindnextfile"></a><a name="findnextfile"></a>CGopher文件查找：：查找下一个文件

调用此成员函数以继续以调用[CGopherFileFind：：：FindFile](#findfile)开始的文件搜索。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>返回值

如果文件更多，则非零;如果找到的文件是目录中的最后一个文件或发生错误，则为零。 要获取扩展错误信息，请致电 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的文件是目录中的最后一个文件，或者找不到匹配的文件，则`GetLastError`函数将返回ERROR_NO_MORE_FILES。

## <a name="cgopherfilefindgetcreationtime"></a><a name="getcreationtime"></a>CGopher文件查找：获取创造时间

获取当前文件的创建时间。

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>参数

*pTimeStamp*<br/>
指向[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构的指针，其中包含创建文件的时间。

*参考时间*<br/>
对[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

### <a name="return-value"></a>返回值

如果成功，则非零;0，如果不成功。 `GetCreationTime`仅当从未在此`CGopherFileFind`对象上调用[FindNextFile](#findnextfile)时，才返回 0。

### <a name="remarks"></a>备注

在调用`GetCreationTime`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性，则此功能可能会返回其他时间戳函数返回的相同值。 有关时间格式的信息，请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上，返回的时间位于文件所在的计算机本地时区。 有关详细信息，请参阅 Win32[文件时间到本地文件时间](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

## <a name="cgopherfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CGopher文件查找：获取最后访问时间

获取上次访问指定文件的时间。

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>参数

*参考时间*<br/>
对[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

*pTimeStamp*<br/>
指向[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构的指针，其中包含上次访问文件的时间。

### <a name="return-value"></a>返回值

如果成功，则非零;0，如果不成功。 `GetLastAccessTime`仅当从未在此`CGopherFileFind`对象上调用[FindNextFile](#findnextfile)时，才返回 0。

### <a name="remarks"></a>备注

在调用`GetLastAccessTime`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性，则此功能可能会返回其他时间戳函数返回的相同值。 有关时间格式的信息，请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上，返回的时间位于文件所在的计算机本地时区。 有关详细信息，请参阅 Win32[文件时间到本地文件时间](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

## <a name="cgopherfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CGopher文件查找：获取最后写入时间

获取上次更改文件的时间。

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>参数

*pTimeStamp*<br/>
指向[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构的指针，其中包含文件上次写入的时间。

*参考时间*<br/>
对[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

### <a name="return-value"></a>返回值

如果成功，则非零;0，如果不成功。 `GetLastWriteTime`仅当从未在此`CGopherFileFind`对象上调用[FindNextFile](#findnextfile)时，才返回 0。

### <a name="remarks"></a>备注

在调用`GetLastWriteTime`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性，则此功能可能会返回其他时间戳函数返回的相同值。 有关时间格式的信息，请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上，返回的时间位于文件所在的计算机本地时区。 有关详细信息，请参阅 Win32[文件时间到本地文件时间](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

## <a name="cgopherfilefindgetlength"></a><a name="getlength"></a>CGopher文件查找：获取长度

调用此成员函数以获取找到文件的长度（以字节为单位）。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>返回值

找到文件的长度（以字节为单位）。

### <a name="remarks"></a>备注

`GetLength`使用 Win32 结构[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)获取以字节为单位的文件大小的值。

> [!NOTE]
> 自 MFC 7.0`GetLength`起，支持 64 位整数类型。 以前使用此较新版本的库构建的代码可能会导致截断警告。

### <a name="example"></a>示例

  请参阅[CFile：：getLength（](../../mfc/reference/cfile-class.md#getlength)基类实现）的示例。

## <a name="cgopherfilefindgetlocator"></a><a name="getlocator"></a>CGopher文件查找：获取定位器

调用此成员函数获取[FindFile](#findfile)用于查找 gopher 文件的[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>返回值

`CGopherLocator` 对象。

## <a name="cgopherfilefindgetscreenname"></a><a name="getscreenname"></a>CGopher文件查找：获取屏幕名称

调用此成员函数获取高时屏幕的名称。

```
CString GetScreenName() const;
```

### <a name="return-value"></a>返回值

高舍屏幕的名称。

## <a name="cgopherfilefindisdots"></a><a name="isdots"></a>CGopher文件查找：：是点

测试当前目录和父目录标记，同时遍历文件。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>返回值

如果找到的文件的名称为"."或".."，则为".."，表示找到的文件实际上是一个目录，则为非零。 否则 0。

### <a name="remarks"></a>备注

在调用`IsDots`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

## <a name="see-also"></a>另请参阅

[CFileFind 类](../../mfc/reference/cfilefind-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind 类](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind 类](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 类](../../mfc/reference/chttpfile-class.md)
