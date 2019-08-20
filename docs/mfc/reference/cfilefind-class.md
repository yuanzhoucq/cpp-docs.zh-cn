---
title: CFileFind 类
ms.date: 11/04/2016
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
ms.openlocfilehash: 2ec8c50a317a09e97a212e8cd7b9be1b58272af9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506574"
---
# <a name="cfilefind-class"></a>CFileFind 类

执行本地文件搜索, 并且是执行 Internet 文件搜索的[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)的基类。

## <a name="syntax"></a>语法

```
class CFileFind : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|构造 `CFileFind` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CFileFind::Close](#close)|关闭搜索请求。|
|[CFileFind::FindFile](#findfile)|在目录中搜索指定的文件名。|
|[CFileFind::FindNextFile](#findnextfile)|继续对[FindFile](#findfile)进行的文件搜索。|
|[CFileFind::GetCreationTime](#getcreationtime)|获取文件的创建时间。|
|[CFileFind::GetFileName](#getfilename)|获取找到的文件的名称 (包括扩展名)|
|[CFileFind::GetFilePath](#getfilepath)|获取找到的文件的完整路径。|
|[CFileFind::GetFileTitle](#getfiletitle)|获取找到的文件的标题。 标题不包含扩展名。|
|[CFileFind::GetFileURL](#getfileurl)|获取找到的文件的 URL, 包括文件路径。|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|获取上次访问文件的时间。|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|获取上次更改和保存文件的时间。|
|[CFileFind::GetLength](#getlength)|获取找到的文件的长度 (以字节为单位)。|
|[CFileFind::GetRoot](#getroot)|获取找到的文件的根目录。|
|[CFileFind::IsArchived](#isarchived)|确定找到的文件是否已存档。|
|[CFileFind::IsCompressed](#iscompressed)|确定找到的文件是否已压缩。|
|[CFileFind::IsDirectory](#isdirectory)|确定找到的文件是否为目录。|
|[CFileFind::IsDots](#isdots)|确定找到的文件的名称是否具有名称 "." 或 "...", 以指示实际上是一个目录。|
|[CFileFind::IsHidden](#ishidden)|确定找到的文件是否处于隐藏状态。|
|[CFileFind::IsNormal](#isnormal)|确定找到的文件是否是正常的 (换言之, 没有其他属性)。|
|[CFileFind::IsReadOnly](#isreadonly)|确定找到的文件是否为只读。|
|[CFileFind::IsSystem](#issystem)|确定找到的文件是否为系统文件。|
|[CFileFind::IsTemporary](#istemporary)|确定找到的文件是否为临时文件。|
|[CFileFind::MatchesMask](#matchesmask)|指示要查找的文件的所需文件属性。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|关闭当前搜索句柄指定的文件。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|指向 `CAtlTransactionManager` 对象的指针。|

## <a name="remarks"></a>备注

`CFileFind`包括开始搜索、查找文件以及返回文件的标题、名称或路径的成员函数。 对于 Internet 搜索, 成员函数[GetFileURL](#getfileurl)返回文件的 URL。

`CFileFind`用于搜索特定服务器类型的其他两个 MFC 类的基类: `CGopherFileFind`专用于 gopher 服务器, 并`CFtpFileFind`专用于 FTP 服务器。 这三个类共同提供了一个无缝机制, 使客户端能够在本地计算机或远程服务器上查找文件, 而不考虑服务器协议、文件类型或位置。

下面的代码将枚举当前目录中的所有文件, 并打印每个文件的名称:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

为了简单起见, 此代码使用C++标准库`cout`类。 例如, 在具有图形用户界面的程序`CListBox::AddString`中, 可以使用调用来替换该行。`cout`

有关如何使用`CFileFind`和其他 WinInet 类的详细信息, 请参阅文章[使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="cfilefind"></a>  CFileFind::CFileFind

构造`CFileFind`对象时, 将调用此成员函数。

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>参数

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="example"></a>示例

  请参阅[CFileFind:: GetFileName](#getfilename)的示例。

##  <a name="close"></a>  CFileFind::Close

调用此成员函数以结束搜索、重置上下文并释放所有资源。

```
void Close();
```

### <a name="remarks"></a>备注

调用`Close`后, 在调用[FindFile](#findfile)之前, 无需创建`CFileFind`新的实例即可开始新的搜索。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetFileName](#getfilename)的示例。

##  <a name="closecontext"></a>  CFileFind::CloseContext

关闭当前搜索句柄指定的文件。

```
virtual void CloseContext();
```

### <a name="remarks"></a>备注

关闭搜索句柄的当前值所指定的文件。 重写此函数以更改默认行为。

必须至少调用[FindFile](#findfile)或[FindNextFile](#findnextfile)函数一次, 才能检索有效的搜索句柄。 `FindFile` 和`FindNextFile`函数使用搜索句柄来查找名称与给定名称匹配的文件。

##  <a name="findfile"></a>  CFileFind::FindFile

调用此成员函数以打开文件搜索。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>参数

*pstrName*<br/>
指向字符串的指针, 该字符串包含要查找的文件的名称。 如果为*pstrName*传递 NULL, `FindFile`将执行通配符 (*.\*) 搜索。

*dwUnused*<br/>
保留以使`FindFile`派生类成为多态。 必须为 0。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 若要获得扩展的错误信息, 请调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>备注

在调用`FindFile`开始文件搜索后, 调用[FindNextFile](#findnextfile)检索后续文件。 在调用以下`FindNextFile`任何属性成员函数之前, 必须至少调用一次:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

### <a name="example"></a>示例

  请参阅[CFileFind:: IsDirectory](#isdirectory)的示例。

##  <a name="findnextfile"></a>  CFileFind::FindNextFile

调用此成员函数以从以前对[FindFile](#findfile)的调用继续执行文件搜索。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>返回值

如果有多个文件, 则为非零值;如果找到的文件是目录中的最后一个, 或者如果出现错误, 则为零。 若要获得扩展的错误信息, 请调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的文件是目录中的最后一个文件, 或者找不到匹配的文件, 则该`GetLastError`函数将返回 ERROR_NO_MORE_FILES。

### <a name="remarks"></a>备注

在调用以下`FindNextFile`任何属性成员函数之前, 必须至少调用一次:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

`FindNextFile`包装 Win32 函数[FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)。

### <a name="example"></a>示例

  请参阅[CFileFind:: IsDirectory](#isdirectory)的示例。

##  <a name="getcreationtime"></a>  CFileFind::GetCreationTime

调用此成员函数可获取指定文件的创建时间。

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

如果成功, 则为非零值;如果不成功, 则为0。 `GetCreationTime`仅当从未在此`CFileFind`对象上调用 [FindNextFile](#findnextfile) 时返回0。

### <a name="remarks"></a>备注

在调用`GetCreationTime`之前, 必须至少调用[FindNextFile](#findnextfile) 。

> [!NOTE]
>  并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性, 则此函数返回的值可能与其他时间戳函数返回的值相同。 有关时间格式的信息, 请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上, 返回的时间是该文件所在的计算机的本地时区。 有关详细信息, 请参阅 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetLength](#getlength)的示例。

##  <a name="getfilename"></a>  CFileFind::GetFileName

调用此成员函数以获取找到的文件的名称。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>返回值

最近找到的文件的名称。

### <a name="remarks"></a>备注

调用 GetFileName 前, 必须至少调用一次[FindNextFile](#findnextfile) 。

`GetFileName`是返回某种格式`CFileFind`的文件名的三个成员函数之一。 下面的列表描述了三种方法和它们之间的区别:

- `GetFileName`返回文件名 (包括扩展名)。 例如, 调用`GetFileName`以生成有关文件*c:\myhtml\myfile.txt*的用户消息将返回文件名*myfile.txt*。

- [GetFilePath](#getfilepath)返回文件的整个路径。 例如, 调用`GetFilePath`以生成有关文件*c:\myhtml\myfile.txt*的用户消息将返回文件路径*c:\myhtml\myfile.txt*。

- [GetFileTitle](#getfiletitle)返回文件名, 不包括文件扩展名。 例如, 调用`GetFileTitle`以生成有关文件*c:\myhtml\myfile.txt*的用户消息将返回文件标题*myfile.txt*。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

##  <a name="getfilepath"></a>  CFileFind::GetFilePath

调用此成员函数以获取指定文件的完整路径。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>返回值

指定文件的路径。

### <a name="remarks"></a>备注

在调用`GetFilePath`之前, 必须至少调用[FindNextFile](#findnextfile) 。

`GetFilePath`是返回某种格式`CFileFind`的文件名的三个成员函数之一。 下面的列表描述了三种方法和它们之间的区别:

- [GetFileName](#getfilename)返回文件名 (包括扩展名)。 例如, 调用`GetFileName`以生成有关文件*c:\myhtml\myfile.txt*的用户消息将返回文件名*myfile.txt*。

- `GetFilePath`返回文件的整个路径。 例如, 调用`GetFilePath`以生成有关文件`c:\myhtml\myfile.txt`的用户消息将返回文件路径`c:\myhtml\myfile.txt`。

- [GetFileTitle](#getfiletitle)返回文件名, 不包括文件扩展名。 例如, 调用`GetFileTitle`以生成有关文件*c:\myhtml\myfile.txt*的用户消息将返回文件标题*myfile.txt*。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetFileName](#getfilename)的示例。

##  <a name="getfiletitle"></a>  CFileFind::GetFileTitle

调用此成员函数以获取找到的文件的标题。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>返回值

文件的标题。

### <a name="remarks"></a>备注

在调用`GetFileTitle`之前, 必须至少调用[FindNextFile](#findnextfile) 。

`GetFileTitle`是返回某种格式`CFileFind`的文件名的三个成员函数之一。 下面的列表描述了三种方法和它们之间的区别:

- [GetFileName](#getfilename)返回文件名 (包括扩展名)。 例如, 调用`GetFileName`以生成有关文件*c:\myhtml\myfile.txt*的用户消息将返回文件名*myfile.txt*。

- [GetFilePath](#getfilepath)返回文件的整个路径。 例如, 调用`GetFilePath`以生成有关文件*c:\myhtml\myfile.txt*的用户消息将返回文件路径*c:\myhtml\myfile.txt*。

- `GetFileTitle`返回文件名, 不包括文件扩展名。 例如, 调用`GetFileTitle`以生成有关文件*c:\myhtml\myfile.txt*的用户消息将返回文件标题*myfile.txt*。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetFileName](#getfilename)的示例。

##  <a name="getfileurl"></a>  CFileFind::GetFileURL

调用此成员函数以检索指定的 URL。

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>返回值

完整的 URL。

### <a name="remarks"></a>备注

在调用`GetFileURL`之前, 必须至少调用[FindNextFile](#findnextfile) 。

`GetFileURL`与成员函数[GetFilePath](#getfilepath)类似, 不同之处在于它以形式`file://path`返回 URL。 例如, 调用`GetFileURL`以获取*myfile.txt*的完整 url 返回 url `file://c:\myhtml\myfile.txt`。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetFileName](#getfilename)的示例。

##  <a name="getlastaccesstime"></a>  CFileFind::GetLastAccessTime

调用此成员函数以获取上次访问指定文件的时间。

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

如果成功, 则为非零值;如果不成功, 则为0。 `GetLastAccessTime`仅当从未在此`CFileFind`对象上调用 [FindNextFile](#findnextfile) 时返回0。

### <a name="remarks"></a>备注

在调用`GetLastAccessTime`之前, 必须至少调用[FindNextFile](#findnextfile) 。

> [!NOTE]
>  并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性, 则此函数返回的值可能与其他时间戳函数返回的值相同。 有关时间格式的信息, 请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上, 返回的时间是该文件所在的计算机的本地时区。 有关详细信息, 请参阅 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetLength](#getlength)的示例。

##  <a name="getlastwritetime"></a>  CFileFind::GetLastWriteTime

调用此成员函数以获取文件上次更改的时间。

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

如果成功, 则为非零值;如果不成功, 则为0。 `GetLastWriteTime`仅当从未在此`CFileFind`对象上调用 [FindNextFile](#findnextfile) 时返回0。

### <a name="remarks"></a>备注

在调用`GetLastWriteTime`之前, 必须至少调用[FindNextFile](#findnextfile) 。

> [!NOTE]
>  并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性, 则此函数返回的值可能与其他时间戳函数返回的值相同。 有关时间格式的信息, 请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上, 返回的时间是该文件所在的计算机的本地时区。 有关详细信息, 请参阅 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetLength](#getlength)的示例。

##  <a name="getlength"></a>  CFileFind::GetLength

调用此成员函数以获取找到的文件的长度 (以字节为单位)。

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>返回值

找到的文件的长度 (以字节为单位)。

### <a name="remarks"></a>备注

在调用`GetLength`之前, 必须至少调用[FindNextFile](#findnextfile) 。

`GetLength`使用 Win32 结构[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)获取并返回文件大小的值 (以字节为单位)。

> [!NOTE]
>  在 MFC 7.0 中, `GetLength`支持64位整数类型。 以前用此更新版本的库生成的现有代码可能会导致截断警告。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

##  <a name="getroot"></a>  CFileFind::GetRoot

调用此成员函数以获取找到的文件的根。

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>返回值

活动搜索的根。

### <a name="remarks"></a>备注

在调用`GetRoot`之前, 必须至少调用[FindNextFile](#findnextfile) 。

此成员函数返回用于启动搜索的驱动器说明符和路径名。 例如, 在`*.dat` `GetRoot`调用[FindFile](#findfile)时, 将返回一个空字符串。 `c:\windows\system\*.dll`将路径 (如) 传递给`FindFile`返回`c:\windows\system\`的`GetRoot`结果。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetFileName](#getfilename)的示例。

##  <a name="isarchived"></a>  CFileFind::IsArchived

调用此成员函数以确定所找到的文件是否已存档。

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

应用程序使用 FILE_ATTRIBUTE_ARCHIVE (在[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性) 标记要备份或删除的存档文件。

在调用`IsArchived`之前, 必须至少调用[FindNextFile](#findnextfile) 。

有关文件属性的完整列表, 请参阅成员函数[MatchesMask](#matchesmask) 。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetLength](#getlength)的示例。

##  <a name="iscompressed"></a>  CFileFind::IsCompressed

调用此成员函数以确定所找到的文件是否已压缩。

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

压缩文件标记有 FILE_ATTRIBUTE_COMPRESSED, 这是在[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性。 对于文件, 此属性表示文件中的所有数据都已压缩。 对于目录, 此属性指示压缩是新创建的文件和子目录的默认值。

在调用`IsCompressed`之前, 必须至少调用[FindNextFile](#findnextfile) 。

有关文件属性的完整列表, 请参阅成员函数[MatchesMask](#matchesmask) 。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetLength](#getlength)的示例。

##  <a name="isdirectory"></a>  CFileFind::IsDirectory

调用此成员函数以确定所找到的文件是否为目录。

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

作为目录的文件用 FILE_ATTRIBUTE_DIRECTORY 标记[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性。

在调用`IsDirectory`之前, 必须至少调用[FindNextFile](#findnextfile) 。

有关文件属性的完整列表, 请参阅成员函数[MatchesMask](#matchesmask) 。

### <a name="example"></a>示例

此小程序 recurses 在 C:\ 上的每个目录驱动器并打印目录的名称。

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

##  <a name="isdots"></a>  CFileFind::IsDots

调用此成员函数可在循环访问文件时测试当前目录和父目录标记。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>返回值

如果找到的文件的名称为 "." 或 "..", 则为非零值, 表示找到的文件实际上是一个目录。 否则为0。

### <a name="remarks"></a>备注

在调用`IsDots`之前, 必须至少调用[FindNextFile](#findnextfile) 。

### <a name="example"></a>示例

  请参阅[CFileFind:: IsDirectory](#isdirectory)的示例。

##  <a name="ishidden"></a>  CFileFind::IsHidden

调用此成员函数以确定所找到的文件是否隐藏。

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

用 FILE_ATTRIBUTE_HIDDEN 标记的隐藏文件, 在[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性。 普通目录列表中不包含隐藏的文件。

在调用`IsHidden`之前, 必须至少调用[FindNextFile](#findnextfile) 。

有关文件属性的完整列表, 请参阅成员函数[MatchesMask](#matchesmask) 。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetLength](#getlength)的示例。

##  <a name="isnormal"></a>  CFileFind::IsNormal

调用此成员函数以确定所找到的文件是否为常规文件。

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

标记有 FILE_ATTRIBUTE_NORMAL 的文件, [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性。 普通文件未设置其他属性。 所有其他文件属性都覆盖此属性。

在调用`IsNormal`之前, 必须至少调用[FindNextFile](#findnextfile) 。

有关文件属性的完整列表, 请参阅成员函数[MatchesMask](#matchesmask) 。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetLength](#getlength)的示例。

##  <a name="isreadonly"></a>  CFileFind::IsReadOnly

调用此成员函数以确定所找到的文件是否为只读。

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

只读文件标记有 FILE_ATTRIBUTE_READONLY, 这是在[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性。 应用程序可以读取这样的文件, 但不能写入或删除它。

在调用`IsReadOnly`之前, 必须至少调用[FindNextFile](#findnextfile) 。

有关文件属性的完整列表, 请参阅成员函数[MatchesMask](#matchesmask) 。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetLength](#getlength)的示例。

##  <a name="issystem"></a>  CFileFind::IsSystem

调用此成员函数以确定所找到的文件是否为系统文件。

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

系统文件使用 FILE_ATTRIBUTE_SYSTEM、、 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性进行标记。 系统文件是的一部分, 或由操作系统独占使用。

在调用`IsSystem`之前, 必须至少调用[FindNextFile](#findnextfile) 。

有关文件属性的完整列表, 请参阅成员函数[MatchesMask](#matchesmask) 。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetLength](#getlength)的示例。

##  <a name="istemporary"></a>  CFileFind::IsTemporary

调用此成员函数以确定所找到的文件是否为临时文件。

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

临时文件标记有 FILE_ATTRIBUTE_TEMPORARY, 这是在[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性。 临时文件用于临时存储。 应用程序只有在绝对必要时才应写入文件。 文件中的大部分数据都将保留在内存中, 而不会被刷新到媒体上, 因为此文件即将被删除。

在调用`IsTemporary`之前, 必须至少调用[FindNextFile](#findnextfile) 。

有关文件属性的完整列表, 请参阅成员函数[MatchesMask](#matchesmask) 。

### <a name="example"></a>示例

  请参阅[CFileFind:: GetLength](#getlength)的示例。

##  <a name="m_ptm"></a>  CFileFind::m_pTM

指向 `CAtlTransactionManager` 对象的指针。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>备注

##  <a name="matchesmask"></a>  CFileFind::MatchesMask

调用此成员函数以测试找到的文件上的文件特性。

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>参数

*dwMask*<br/>
为找到的文件指定一个或多个[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性。 若要搜索多个属性, 请使用按位&#124;or () 运算符。 以下属性的任意组合都是可接受的:

- FILE_ATTRIBUTE_ARCHIVE 文件是存档文件。 应用程序使用此属性将文件标记为备份或删除。

- FILE_ATTRIBUTE_COMPRESSED 文件或目录已压缩。 对于文件, 这意味着文件中的所有数据都已压缩。 对于目录, 这意味着压缩是新创建的文件和子目录的默认值。

- FILE_ATTRIBUTE_DIRECTORY 该文件是一个目录。

- FILE_ATTRIBUTE_NORMAL 文件未设置其他属性。 仅当单独使用时, 此特性才有效。 所有其他文件属性都覆盖此属性。

- FILE_ATTRIBUTE_HIDDEN 文件处于隐藏状态。 它不会包含在普通目录列表中。

- FILE_ATTRIBUTE_READONLY 文件为只读。 应用程序可以读取该文件, 但不能写入或删除它。

- FILE_ATTRIBUTE_SYSTEM 文件是的一部分, 或者被操作系统独占使用。

- FILE_ATTRIBUTE_TEMPORARY 文件用于临时存储。 应用程序只有在绝对必要时才应写入文件。 文件中的大部分数据都将保留在内存中, 而不会被刷新到媒体上, 因为此文件即将被删除。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 若要获得扩展的错误信息, 请调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>备注

在调用`MatchesMask`之前, 必须至少调用[FindNextFile](#findnextfile) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind 类](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopherFileFind 类](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 类](../../mfc/reference/chttpfile-class.md)
