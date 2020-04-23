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
ms.openlocfilehash: 5bb53a6abf7040bd6ee9f5f2cf56b0feb4d62e66
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755029"
---
# <a name="cfilefind-class"></a>CFileFind 类

执行本地文件搜索，是执行 Internet 文件搜索的[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)的基本类。

## <a name="syntax"></a>语法

```
class CFileFind : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[文件查找：：文件查找](#cfilefind)|构造 `CFileFind` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[文件查找：关闭](#close)|关闭搜索请求。|
|[文件查找：查找文件](#findfile)|搜索目录以搜索指定的文件名。|
|[文件查找：：查找下一个文件](#findnextfile)|继续从上一个调用[FindFile](#findfile)的文件搜索。|
|[文件查找：获取创作时间](#getcreationtime)|获取创建文件的时间。|
|[文件查找：：获取文件名](#getfilename)|获取找到文件的名称（包括扩展名）|
|[文件查找：获取文件路径](#getfilepath)|获取找到文件的整个路径。|
|[文件查找：获取文件标题](#getfiletitle)|获取找到文件的标题。 标题不包括扩展。|
|[文件查找：：获取文件URL](#getfileurl)|获取找到文件的 URL，包括文件路径。|
|[文件查找：：获取最后访问时间](#getlastaccesstime)|获取上次访问文件的时间。|
|[文件查找：：获取最后写入时间](#getlastwritetime)|获取上次更改和保存文件的时间。|
|[文件查找：获取长度](#getlength)|获取找到文件的长度（以字节为单位）。|
|[文件查找：获取根](#getroot)|获取找到文件的根目录。|
|[文件查找：已存档](#isarchived)|确定是否存档了找到的文件。|
|[文件查找：已压缩](#iscompressed)|确定是否压缩找到的文件。|
|[文件查找：：IsDirectory](#isdirectory)|确定找到的文件是否为目录。|
|[文件查找：：是点](#isdots)|确定找到的文件的名称是否具有名称"."或".."，指示该文件实际上是一个目录。|
|[文件查找：隐藏](#ishidden)|确定找到的文件是否隐藏。|
|[文件查找：：正常](#isnormal)|确定找到的文件是否正常（换句话说，没有其他属性）。|
|[文件查找：仅阅读](#isreadonly)|确定找到的文件是否为只读文件。|
|[文件查找：isSystem](#issystem)|确定找到的文件是否为系统文件。|
|[文件查找：：临时](#istemporary)|确定找到的文件是否临时。|
|[文件查找：：匹配蒙版](#matchesmask)|指示要找到的文件所需的文件属性。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[文件查找：：关闭上下文](#closecontext)|关闭当前搜索句柄指定的文件。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[文件查找：m_pTM](#m_ptm)|指向 `CAtlTransactionManager` 对象的指针。|

## <a name="remarks"></a>备注

`CFileFind`包括开始搜索、查找文件并返回文件的标题、名称或路径的成员函数。 对于 Internet 搜索，成员函数[GetFileURL](#getfileurl)返回文件的 URL。

`CFileFind`是另外两个 MFC 类的基本类，旨在搜索特定的服务器类型`CGopherFileFind`：专门使用 gopher 服务器`CFtpFileFind`，并特别适用于 FTP 服务器。 总之，这三个类为客户端提供了一个无缝机制，以便客户端查找本地计算机或远程服务器上的文件，而不管服务器协议、文件类型或位置如何。

以下代码将枚举当前目录中的所有文件，打印每个文件的名称：

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

为了保持示例简单，此代码使用C++标准库`cout`类。 线路`cout`可以替换为调用`CListBox::AddString`，例如，在具有图形用户界面的程序中。

有关如何使用`CFileFind`和其他 WinInet 类的详细信息，请参阅[使用 WinInet 进行 Internet 编程的文章](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cfilefindcfilefind"></a><a name="cfilefind"></a>文件查找：：文件查找

构造`CFileFind`对象时将调用此成员函数。

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>参数

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="example"></a>示例

  请参阅[CFileFind 示例：获取文件名](#getfilename)。

## <a name="cfilefindclose"></a><a name="close"></a>文件查找：关闭

调用此成员函数以结束搜索、重置上下文并释放所有资源。

```cpp
void Close();
```

### <a name="remarks"></a>备注

调用`Close`后，您不必在调用`CFileFind`[FindFile](#findfile)开始新搜索之前创建新实例。

### <a name="example"></a>示例

  请参阅[CFileFind 示例：获取文件名](#getfilename)。

## <a name="cfilefindclosecontext"></a><a name="closecontext"></a>文件查找：：关闭上下文

关闭当前搜索句柄指定的文件。

```
virtual void CloseContext();
```

### <a name="remarks"></a>备注

关闭搜索句柄的当前值指定的文件。 重写此函数以更改默认行为。

您必须至少调用一次[FindFile](#findfile)或[FindNextFile](#findnextfile)函数才能检索有效的搜索句柄。 `FindFile`和`FindNextFile`函数使用搜索句柄查找名称与给定名称匹配的文件。

## <a name="cfilefindfindfile"></a><a name="findfile"></a>文件查找：查找文件

调用此成员函数以打开文件搜索。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>参数

*pstrName*<br/>
指向要查找的文件名称的字符串的指针。 如果通过 NULL 进行*pstrName，*`FindFile`则执行通配符\*（*） 搜索。

*dwunused*<br/>
保留以使用`FindFile`派生类进行多态性。 必须为 0。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 要获取扩展错误信息，请致电 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>备注

调用`FindFile`开始文件搜索后，调用[FindNextFile](#findnextfile)检索后续文件。 在调用以下`FindNextFile`任一属性成员函数之前，必须至少调用一次：

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [获取文件标题](#getfiletitle)

- [获取文件路径](#getfilepath)

- [获取文件URL](#getfileurl)

- [获取最后访问时间](#getlastaccesstime)

- [获取上次写入时间](#getlastwritetime)

- [获取长度](#getlength)

- [GetRoot](#getroot)

- [已存档](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [是点](#isdots)

- [已隐藏](#ishidden)

- [正常](#isnormal)

- [仅阅读](#isreadonly)

- [IsSystem](#issystem)

- [临时性](#istemporary)

- [匹配蒙版](#matchesmask)

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：isDirectory](#isdirectory)。

## <a name="cfilefindfindnextfile"></a><a name="findnextfile"></a>文件查找：：查找下一个文件

调用此成员函数以继续从之前调用[FindFile](#findfile)的文件搜索。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>返回值

如果文件更多，则非零;如果找到的文件是目录中的最后一个文件或发生错误，则为零。 要获取扩展错误信息，请致电 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的文件是目录中的最后一个文件，或者找不到匹配的文件，则`GetLastError`函数将返回ERROR_NO_MORE_FILES。

### <a name="remarks"></a>备注

在调用以下`FindNextFile`任一属性成员函数之前，必须至少调用一次：

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [获取文件标题](#getfiletitle)

- [获取文件路径](#getfilepath)

- [获取文件URL](#getfileurl)

- [获取最后访问时间](#getlastaccesstime)

- [获取上次写入时间](#getlastwritetime)

- [获取长度](#getlength)

- [GetRoot](#getroot)

- [已存档](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [是点](#isdots)

- [已隐藏](#ishidden)

- [正常](#isnormal)

- [仅阅读](#isreadonly)

- [IsSystem](#issystem)

- [临时性](#istemporary)

- [匹配蒙版](#matchesmask)

`FindNextFile`包装 Win32 函数[FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：isDirectory](#isdirectory)。

## <a name="cfilefindgetcreationtime"></a><a name="getcreationtime"></a>文件查找：获取创作时间

调用此成员函数以获取创建指定文件的时间。

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

如果成功，则非零;0，如果不成功。 `GetCreationTime`仅当从未在此`CFileFind`对象上调用[FindNextFile](#findnextfile)时，才返回 0。

### <a name="remarks"></a>备注

在调用`GetCreationTime`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性，则此功能可能会返回其他时间戳函数返回的相同值。 有关时间格式的信息，请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上，返回的时间位于文件所在的计算机本地时区。 有关详细信息，请参阅 Win32[文件时间到本地文件时间](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：获取长度](#getlength)。

## <a name="cfilefindgetfilename"></a><a name="getfilename"></a>文件查找：：获取文件名

调用此成员函数以获取找到的文件的名称。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>返回值

最近找到的文件的名称。

### <a name="remarks"></a>备注

在调用 GetFileName 之前，您必须至少调用一次[FindNextFile。](#findnextfile)

`GetFileName`是返回某种形式的文件`CFileFind`名的三个成员函数之一。 下面的列表描述了这三者及其变化方式：

- `GetFileName`返回文件名，包括扩展名。 例如，调用`GetFileName`以生成有关文件*c：_myhtml_myfile.txt*的用户消息返回文件名*myfile.txt*。

- [GetFilePath](#getfilepath)返回文件的整个路径。 例如，调用`GetFilePath`以生成有关文件*c：_myhtml_myfile.txt*的用户消息返回文件路径*c：\myhtml_myfile.txt*。

- [GetFileTitle](#getfiletitle)返回文件名，不包括文件扩展名。 例如，调用`GetFileTitle`以生成有关文件*c：_myhtml_myfile.txt*的用户消息返回文件标题*myfile*。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

## <a name="cfilefindgetfilepath"></a><a name="getfilepath"></a>文件查找：获取文件路径

调用此成员函数获取指定文件的完整路径。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>返回值

指定文件的路径。

### <a name="remarks"></a>备注

在调用`GetFilePath`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

`GetFilePath`是返回某种形式的文件`CFileFind`名的三个成员函数之一。 下面的列表描述了这三者及其变化方式：

- [GetFileName](#getfilename)返回文件名，包括扩展名。 例如，调用`GetFileName`以生成有关文件*c：_myhtml_myfile.txt*的用户消息返回文件名*myfile.txt*。

- `GetFilePath`返回文件的整个路径。 例如，调用`GetFilePath`以生成有关该文件`c:\myhtml\myfile.txt`的用户消息将返回文件路径`c:\myhtml\myfile.txt`。

- [GetFileTitle](#getfiletitle)返回文件名，不包括文件扩展名。 例如，调用`GetFileTitle`以生成有关文件*c：_myhtml_myfile.txt*的用户消息返回文件标题*myfile*。

### <a name="example"></a>示例

  请参阅[CFileFind 示例：获取文件名](#getfilename)。

## <a name="cfilefindgetfiletitle"></a><a name="getfiletitle"></a>文件查找：获取文件标题

调用此成员函数获取找到的文件的标题。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>返回值

文件的标题。

### <a name="remarks"></a>备注

在调用`GetFileTitle`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

`GetFileTitle`是返回某种形式的文件`CFileFind`名的三个成员函数之一。 下面的列表描述了这三者及其变化方式：

- [GetFileName](#getfilename)返回文件名，包括扩展名。 例如，调用`GetFileName`以生成有关文件*c：_myhtml_myfile.txt*的用户消息返回文件名*myfile.txt*。

- [GetFilePath](#getfilepath)返回文件的整个路径。 例如，调用`GetFilePath`以生成有关文件*c：_myhtml_myfile.txt*的用户消息返回文件路径*c：\myhtml_myfile.txt*。

- `GetFileTitle`返回文件名，不包括文件扩展名。 例如，调用`GetFileTitle`以生成有关文件*c：_myhtml_myfile.txt*的用户消息返回文件标题*myfile*。

### <a name="example"></a>示例

  请参阅[CFileFind 示例：获取文件名](#getfilename)。

## <a name="cfilefindgetfileurl"></a><a name="getfileurl"></a>文件查找：：获取文件URL

调用此成员函数以检索指定的 URL。

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>返回值

完整的 URL。

### <a name="remarks"></a>备注

在调用`GetFileURL`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

`GetFileURL`与成员函数[GetFilePath](#getfilepath)类似，只不过它返回窗体`file://path`中的 URL。 例如，调用`GetFileURL`以获取*myfile.txt*的完整 URL 返回`file://c:\myhtml\myfile.txt`URL 。

### <a name="example"></a>示例

  请参阅[CFileFind 示例：获取文件名](#getfilename)。

## <a name="cfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>文件查找：：获取最后访问时间

调用此成员函数以获取上次访问指定文件的时间。

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

如果成功，则非零;0，如果不成功。 `GetLastAccessTime`仅当从未在此`CFileFind`对象上调用[FindNextFile](#findnextfile)时，才返回 0。

### <a name="remarks"></a>备注

在调用`GetLastAccessTime`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性，则此功能可能会返回其他时间戳函数返回的相同值。 有关时间格式的信息，请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上，返回的时间位于文件所在的计算机本地时区。 有关详细信息，请参阅 Win32[文件时间到本地文件时间](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：获取长度](#getlength)。

## <a name="cfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>文件查找：：获取最后写入时间

调用此成员函数以获取上次更改文件的时间。

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

如果成功，则非零;0，如果不成功。 `GetLastWriteTime`仅当从未在此`CFileFind`对象上调用[FindNextFile](#findnextfile)时，才返回 0。

### <a name="remarks"></a>备注

在调用`GetLastWriteTime`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 并非所有文件系统都使用相同的语义来实现此函数返回的时间戳。 如果基础文件系统或服务器不支持保留时间属性，则此功能可能会返回其他时间戳函数返回的相同值。 有关时间格式的信息，请参阅[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构。 在某些操作系统上，返回的时间位于文件所在的计算机本地时区。 有关详细信息，请参阅 Win32[文件时间到本地文件时间](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：获取长度](#getlength)。

## <a name="cfilefindgetlength"></a><a name="getlength"></a>文件查找：获取长度

调用此成员函数以获取找到的文件的长度（以字节为单位）。

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>返回值

找到文件的长度（以字节为单位）。

### <a name="remarks"></a>备注

在调用`GetLength`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

`GetLength`使用 Win32 结构[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)获取和返回文件大小的值（以字节为单位）。

> [!NOTE]
> 自 MFC 7.0`GetLength`起，支持 64 位整数类型。 以前使用此较新版本的库构建的现有代码可能会导致截断警告。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

## <a name="cfilefindgetroot"></a><a name="getroot"></a>文件查找：获取根

调用此成员函数以获取找到文件的根。

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>返回值

活动搜索的根。

### <a name="remarks"></a>备注

在调用`GetRoot`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

此成员函数返回用于启动搜索的驱动器指定器和路径名称。 例如，调用[FindFile](#findfile) `*.dat`时会导致`GetRoot`返回空字符串。 将`c:\windows\system\*.dll`路径（如 ）传递给`FindFile`返回`GetRoot``c:\windows\system\`的结果。

### <a name="example"></a>示例

  请参阅[CFileFind 示例：获取文件名](#getfilename)。

## <a name="cfilefindisarchived"></a><a name="isarchived"></a>文件查找：已存档

调用此成员函数以确定找到的文件是否存档。

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

应用程序标记存档文件，该文件将备份或删除[，FILE_ATTRIBUTE_ARCHIVEWIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性。

在调用`IsArchived`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

有关文件属性的完整列表，请参阅成员函数[匹配掩码](#matchesmask)。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：获取长度](#getlength)。

## <a name="cfilefindiscompressed"></a><a name="iscompressed"></a>文件查找：已压缩

调用此成员函数以确定找到的文件是否被压缩。

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

压缩文件标有FILE_ATTRIBUTE_COMPRESSED，WIN32_FIND_DATA[结构中](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)标识的文件属性。 对于文件，此属性指示文件中的所有数据都已压缩。 对于目录，此属性指示压缩是新创建的文件和子目录的默认值。

在调用`IsCompressed`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

有关文件属性的完整列表，请参阅成员函数[匹配掩码](#matchesmask)。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：获取长度](#getlength)。

## <a name="cfilefindisdirectory"></a><a name="isdirectory"></a>文件查找：：IsDirectory

调用此成员函数以确定找到的文件是否为目录。

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

作为目录的文件[FILE_ATTRIBUTE_DIRECTORYWIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性进行标记。

在调用`IsDirectory`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

有关文件属性的完整列表，请参阅成员函数[匹配掩码](#matchesmask)。

### <a name="example"></a>示例

这个小程序会重诅咒 C 上的每个目录：*驱动器并打印目录的名称。

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

## <a name="cfilefindisdots"></a><a name="isdots"></a>文件查找：：是点

调用此成员函数以测试当前目录和父目录标记，同时遍历文件。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>返回值

如果找到的文件的名称为"."或".."，则为".."，表示找到的文件实际上是一个目录，则为非零。 否则 0。

### <a name="remarks"></a>备注

在调用`IsDots`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：isDirectory](#isdirectory)。

## <a name="cfilefindishidden"></a><a name="ishidden"></a>文件查找：隐藏

调用此成员函数以确定找到的文件是否隐藏。

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

隐藏文件（标有FILE_ATTRIBUTE_HIDDEN，WIN32_FIND_DATA[结构中](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)标识的文件属性。 隐藏文件不包括在普通目录列表中。

在调用`IsHidden`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

有关文件属性的完整列表，请参阅成员函数[匹配掩码](#matchesmask)。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：获取长度](#getlength)。

## <a name="cfilefindisnormal"></a><a name="isnormal"></a>文件查找：：正常

调用此成员函数以确定找到的文件是否为普通文件。

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

标有FILE_ATTRIBUTE_NORMAL的文件，WIN32_FIND_DATA[结构中](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)标识的文件属性。 普通文件没有其他属性集。 所有其他文件属性都覆盖此属性。

在调用`IsNormal`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

有关文件属性的完整列表，请参阅成员函数[匹配掩码](#matchesmask)。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：获取长度](#getlength)。

## <a name="cfilefindisreadonly"></a><a name="isreadonly"></a>文件查找：仅阅读

调用此成员函数以确定找到的文件是否为只读文件。

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

只读文件标有FILE_ATTRIBUTE_READONLY，WIN32_FIND_DATA[结构中](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)标识的文件属性。 应用程序可以读取此类文件，但不能写入或删除该文件。

在调用`IsReadOnly`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

有关文件属性的完整列表，请参阅成员函数[匹配掩码](#matchesmask)。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：获取长度](#getlength)。

## <a name="cfilefindissystem"></a><a name="issystem"></a>文件查找：isSystem

调用此成员函数以确定找到的文件是否为系统文件。

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

系统文件标有FILE_ATTRIBUTE_SYSTEM，WIN32_FIND_DATA[结构中](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)标识的文件属性。 系统文件是操作系统的一部分，或者由操作系统专门使用。

在调用`IsSystem`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

有关文件属性的完整列表，请参阅成员函数[匹配掩码](#matchesmask)。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：获取长度](#getlength)。

## <a name="cfilefindistemporary"></a><a name="istemporary"></a>文件查找：：临时

调用此成员函数以确定找到的文件是否为临时文件。

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

临时文件用[FILE_ATTRIBUTE_TEMPORARY（WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识的文件属性）标记。 临时文件用于临时存储。 应用程序仅在绝对必要时才应写入文件。 文件的大部分数据保留在内存中，而不会刷新到介质，因为该文件将很快被删除。

在调用`IsTemporary`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

有关文件属性的完整列表，请参阅成员函数[匹配掩码](#matchesmask)。

### <a name="example"></a>示例

  请参阅[CFileFind 的示例：获取长度](#getlength)。

## <a name="cfilefindm_ptm"></a><a name="m_ptm"></a>文件查找：m_pTM

指向 `CAtlTransactionManager` 对象的指针。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>备注

## <a name="cfilefindmatchesmask"></a><a name="matchesmask"></a>文件查找：：匹配蒙版

调用此成员函数以测试找到的文件上的文件属性。

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>参数

*dwMask*<br/>
为找到的文件指定一个或多个文件属性，这些属性在[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构中标识。 要搜索多个属性，请使用位或（&#124;）运算符。 以下属性的任意组合是可以接受的：

- FILE_ATTRIBUTE_ARCHIVE 该文件是存档文件。 应用程序使用此属性标记文件以进行备份或删除。

- FILE_ATTRIBUTE_COMPRESSED文件或目录被压缩。 对于文件，这意味着文件中的所有数据将被压缩。 对于目录，这意味着压缩是新创建的文件和子目录的默认值。

- FILE_ATTRIBUTE_DIRECTORY 该文件是目录。

- FILE_ATTRIBUTE_NORMAL 该文件没有其他属性集。 此属性仅在单独使用时有效。 所有其他文件属性都覆盖此属性。

- FILE_ATTRIBUTE_HIDDEN文件已隐藏。 它不包含在普通目录列表中。

- FILE_ATTRIBUTE_READONLY该文件是只读的。 应用程序可以读取文件，但不能写入或删除该文件。

- FILE_ATTRIBUTE_SYSTEM 该文件是 操作系统的一部分或由操作系统专门使用。

- FILE_ATTRIBUTE_TEMPORARY 该文件用于临时存储。 应用程序仅在绝对必要时才应写入文件。 文件的大部分数据保留在内存中，而不会刷新到介质，因为该文件将很快被删除。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 要获取扩展错误信息，请致电 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>备注

在调用`MatchesMask`之前，您必须至少调用[FindNextFile](#findnextfile)一次。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind 类](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopher文件查找类](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 类](../../mfc/reference/chttpfile-class.md)
