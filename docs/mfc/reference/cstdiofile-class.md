---
title: CStdioFile 类
ms.date: 08/29/2019
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
ms.openlocfilehash: 4b667f4121d92863335befda3a7beef74f29ad1a
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177490"
---
# <a name="cstdiofile-class"></a>CStdioFile 类

表示由运行时函数[fopen](../../c-runtime-library/reference/fopen-wfopen.md)打开的 C 运行时流文件。

## <a name="syntax"></a>语法

```
class CStdioFile : public CFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|从路径或文件指针构造对象。`CStdioFile`|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CStdioFile::Open](#open)|已重载。 Open 专用于默认`CStdioFile`构造函数（替代[CFile：： Open](../../mfc/reference/cfile-class.md#open)）。|
|[CStdioFile::ReadString](#readstring)|读取一行文本。|
|[CStdioFile::Seek](#seek)|定位当前文件指针。|
|[CStdioFile::WriteString](#writestring)|写入一行文本。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|包含指向打开的文件的指针。|

## <a name="remarks"></a>备注

流文件已缓冲，可以在文本模式（默认值）或二进制模式下打开。

文本模式为回车换行符对提供特殊处理。 将换行符（0x0A）写入文本模式`CStdioFile`对象时，会将字节对（0x0D，0x0A）发送到该文件。 读取时，字节对（0x0D，0x0A）将转换为单个0x0A 字节。

[不支持](../../mfc/reference/cfile-class.md#duplicate) [CFile 函数](../../mfc/reference/cfile-class.md)重复、 [LockRange](../../mfc/reference/cfile-class.md#lockrange)和[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) 。 `CStdioFile`

如果在上`CStdioFile`调用这些函数，则将获得一个[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

`CStdioFile`有关使用的详细信息，请参阅《*运行时库参考*中的文章： [MFC 中的文件](../../mfc/files-in-mfc.md)和[文件处理](../../c-runtime-library/file-handling.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="cstdiofile"></a>CStdioFile：： CStdioFile

构造并初始化一个 `CStdioFile` 对象。

```
CStdioFile();
CStdioFile(CAtlTransactionManager* pTM);
CStdioFile(FILE* pOpenStream);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>参数

*pOpenStream*<br/>
指定通过调用 C 运行时函数[fopen](../../c-runtime-library/reference/fopen-wfopen.md)返回的文件指针。

*lpszFileName*<br/>
指定一个字符串，该字符串是所需文件的路径。 路径可以是相对路径或绝对路径。

*nOpenFlags*<br/>
指定用于文件创建、文件共享和文件访问模式的选项。 您可以使用按位 or （ **|** ）运算符指定多个选项。

需要一个文件访问模式选项;其他模式是可选的。 有关模式选项和其他标志的列表，请参阅[CFile：： CFile](../../mfc/reference/cfile-class.md#cfile) 。 在 MFC 版本3.0 及更高版本中，允许共享标志。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针。

### <a name="remarks"></a>备注

默认构造函数不会将文件附加到`CStdioFile`对象。 使用此构造函数时，必须使用`CStdioFile::Open`方法打开文件并将其附加`CStdioFile`到对象。

单参数构造函数将打开的文件流附加到`CStdioFile`对象。 允许的指针值包括预定义的输入/输出文件指针*stdin*、 *stdout*或*stderr*。

双参数构造函数将创建一个`CStdioFile`对象，并打开具有给定路径的相应文件。

如果为*pOpenStream*或*lpszFileName*传递 NULL，则`CInvalidArgException*`构造函数将引发。

如果文件无法打开或创建，则构造函数将引发`CFileException*`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>CStdioFile：： m_pStream

数据成员是指向由 C 运行时函数`fopen`返回的打开文件的指针。 `m_pStream`

```
FILE* m_pStream;
```

### <a name="remarks"></a>备注

如果文件从未打开或已关闭，则为 NULL。

##  <a name="open"></a>CStdioFile：： Open

已重载。 Open 专用于默认`CStdioFile`构造函数。

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*lpszFileName*<br/>
作为所需文件的路径的字符串。 路径可以是相对路径或绝对路径。

*nOpenFlags*<br/>
共享和访问模式。 指定打开文件时要执行的操作。 可以使用按位 "或" （&#124;）运算符组合选项。 需要一个访问权限和一个共享选项;modeCreate 和 modeNoInherit 模式是可选的。

*pError*<br/>
指向将接收失败操作的状态的现有文件异常对象的指针。

*pTM*<br/>
指向 `CAtlTransactionManager` 对象的指针。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="readstring"></a>CStdioFile：： ReadString

从与`CStdioFile`对象关联的文件中将文本数据读取到缓冲区中，最大值为*n 每天*-1 个字符。

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>参数

*lpsz*<br/>
指定指向用户提供的缓冲区的指针，该缓冲区将接收以 null 结尾的文本字符串。

*nMax*<br/>
指定要读取的最大字符数，不包括终止 null 字符。

*rString*<br/>
对在函数返回`CString`时将包含字符串的对象的引用。

### <a name="return-value"></a>返回值

指向包含文本数据的缓冲区的指针。 如果在未读取任何数据的情况下到达文件尾，则为 NULL;如果已到达文件末尾，则为布尔值; 如果未读取任何数据，则为 FALSE。

### <a name="remarks"></a>备注

读取由第一个换行符停止。 如果在这种情况下，已读取的字符数少于*n 每天*，则在缓冲区中存储一个换行符。 在任一情况下，均追加一个 null 字符（' \ 0 '）。

[CFile：： Read](../../mfc/reference/cfile-class.md#read)也可用于文本模式输入，但不会在回车换行符对上终止。

> [!NOTE]
>  此函数的`'\n'`版本将删除（如果存在）; LPTSTR 版本不会删除。 `CString`

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>CStdioFile：： Seek

在以前打开的文件中重新定位指针。

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>参数

*lOff*<br/>
指针移动的字节数。

*nFrom*<br/>
指针移动模式。 必须是下列值之一：

- `CFile::begin`：将文件指针*lOff*字节从文件开头向前移动。

- `CFile::current`：将文件指针从文件中的当前位置移*lOff*字节。

- `CFile::end`：将文件指针*lOff*字节移到文件末尾。 请注意， *lOff*必须为负数才能查找到现有文件;正值将在文件末尾进行查找。

### <a name="return-value"></a>返回值

如果请求的位置合法， `Seek`则返回从文件开头开始的新字节偏移量。 否则，返回值为 undefined，并引发`CFileException`一个对象。

### <a name="remarks"></a>备注

`Seek`函数可通过将指针移动到指定的量（绝对或相对）来允许对文件内容进行随机访问。 在查找期间，不会实际读取任何数据。 如果请求的位置大于文件的大小，则文件的长度将扩展到该位置，并且不会引发异常。

打开文件时，文件指针将位于文件开头的偏移量0处。

此的`Seek`实现基于运行时库（CRT）函数`fseek`。 在文本模式下打开的流的`Seek`使用有多个限制。 有关详细信息，请参阅[fseek、_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)。

### <a name="example"></a>示例

下面的示例演示如何使用`Seek`在`cfile`文件的开头移动指针1000字节。 请注意，`Seek`不会读取数据，因此必须随后调用[CStdioFile：：ReadString](#readstring)来读取数据。

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>CStdioFile：： WriteString

将缓冲区中的数据写入与`CStdioFile`对象关联的文件。

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>参数

*lpsz*<br/>
指定指向包含以 null 结尾的字符串的缓冲区的指针。

### <a name="remarks"></a>备注

终止的 null 字符（ `\0`）未写入到文件中。 此方法将*lpsz*中的换行符写入文件作为回车换行符对。

如果要将非 null 终止的数据写入文件，请使用`CStdioFile::Write`或[CFile：： write](../../mfc/reference/cfile-class.md#write)。

如果为*lpsz*参数`CInvalidArgException*`指定 NULL，则此方法将引发。

此方法会引发`CFileException*` ，以响应文件系统错误。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>请参阅

[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException 类](../../mfc/reference/cnotsupportedexception-class.md)
