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
ms.openlocfilehash: 80ee65aa339a38b3d8434bc4c7cb977e263f037b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366018"
---
# <a name="cstdiofile-class"></a>CStdioFile 类

表示运行时函数[fopen](../../c-runtime-library/reference/fopen-wfopen.md)打开的 C 运行时流文件。

## <a name="syntax"></a>语法

```
class CStdioFile : public CFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CStdio文件：CStdioFile](#cstdiofile)|从路径或`CStdioFile`文件指针构造对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CStdio文件：打开](#open)|已重载。 打开设计用于与默认`CStdioFile`构造函数（覆盖[文件：：打开](../../mfc/reference/cfile-class.md#open)）。|
|[CStdio文件：阅读字符串](#readstring)|读取一行文本。|
|[CStdio文件：寻找](#seek)|定位当前文件指针。|
|[CStdio文件：写串](#writestring)|写入一行文本。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CStdio文件：m_pStream](#m_pstream)|包含指向打开文件的指针。|

## <a name="remarks"></a>备注

流文件是缓冲的，可以在文本模式（默认）或二进制模式下打开。

文本模式为回车换行对提供特殊处理。 当您将行馈送（换行）字符 （0x0A） 写入文本模式`CStdioFile`对象时，字节对（0x0D，0x0A）将发送到该文件。 读取时，字节对（0x0D，0x0A）将转换为单个 0x0A 字节。

[CFile](../../mfc/reference/cfile-class.md)函数[不支持](../../mfc/reference/cfile-class.md#duplicate)`CStdioFile`重复、[锁定范围](../../mfc/reference/cfile-class.md#lockrange)和[解锁范围](../../mfc/reference/cfile-class.md#unlockrange)。

如果在 上调用这些函数`CStdioFile`，您将获得[CNot 支持异常](../../mfc/reference/cnotsupportedexception-class.md)。

`CStdioFile`有关使用 的详细信息，请参阅[MFC](../../mfc/files-in-mfc.md)中的文章文件和*运行时库参考*中[的文件处理](../../c-runtime-library/file-handling.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cstdiofilecstdiofile"></a><a name="cstdiofile"></a>CStdio文件：CStdioFile

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

*p 开放流*<br/>
指定调用 C 运行时函数[fopen](../../c-runtime-library/reference/fopen-wfopen.md)返回的文件指针。

*lpszFile名称*<br/>
指定作为所需文件的路径的字符串。 路径可以是相对路径或绝对路径。

*nOpenFlags*<br/>
指定文件创建、文件共享和文件访问模式的选项。 可以使用位或 （ ）**|** 运算符指定多个选项。

需要一个文件访问模式选项;其他模式是可选的。 有关模式选项和其他标志的列表，请参阅[CFile：CFile。](../../mfc/reference/cfile-class.md#cfile) 在 MFC 版本 3.0 及更高版本中，允许共享标志。

*pTM*<br/>
指向 CAtl 事务管理器对象的指针。

### <a name="remarks"></a>备注

默认构造函数不将文件附加到`CStdioFile`对象。 使用此构造函数时，`CStdioFile::Open`必须使用 方法打开文件并将其附加到`CStdioFile`对象。

单参数构造函数将打开的文件流附加到`CStdioFile`对象。 允许的指针值包括预定义的输入/输出文件指针*st丁**、stdout*或*stder。*

双参数构造函数创建一个`CStdioFile`对象，并打开具有给定路径的相应文件。

如果为*pOpenStream*或*lpszFileName*传递 NULL，则构造`CInvalidArgException*`函数将引发 。

如果无法打开或创建文件，则构造函数将引发 。 `CFileException*`

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

## <a name="cstdiofilem_pstream"></a><a name="m_pstream"></a>CStdio文件：m_pStream

数据`m_pStream`成员是 C 运行时函数`fopen`返回的指向打开文件的指针。

```
FILE* m_pStream;
```

### <a name="remarks"></a>备注

如果文件从未打开或已关闭，则为 NULL。

## <a name="cstdiofileopen"></a><a name="open"></a>CStdio文件：打开

已重载。 Open 设计用于默认`CStdioFile`构造函数。

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

*lpszFile名称*<br/>
是所需文件的路径的字符串。 路径可以是相对路径或绝对路径。

*nOpenFlags*<br/>
共享和访问模式。 指定打开文件时要执行的操作。 您可以使用位-OR（&#124;）运算符组合选项。 需要一个访问权限和一个共享选项;模式 创建和模式 No 继承模式是可选的。

*pError*<br/>
指向将接收失败操作状态的现有文件异常对象的指针。

*pTM*<br/>
指向 `CAtlTransactionManager` 对象的指针。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="cstdiofilereadstring"></a><a name="readstring"></a>CStdio文件：阅读字符串

从与`CStdioFile`对象关联的文件中将文本数据读取到缓冲区中，最多为*nMax*-1 个字符的限制。

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>参数

*lpsz*<br/>
指定指向用户提供的缓冲区的指针，该缓冲区将接收 null 终止的文本字符串。

*nMax*<br/>
指定要读取的最大字符数，不包括终止空字符。

*rString*<br/>
对在`CString`函数返回时将包含字符串的对象的引用。

### <a name="return-value"></a>返回值

指向包含文本数据的缓冲区的指针。 如果未读取任何数据就到达了文件结尾;或者，如果未读取任何数据就达到文件结尾，则 FALSE。

### <a name="remarks"></a>备注

读取由第一个领线字符停止。 在这种情况下，如果读取的字符少于*nMax*-1 字符，则缓冲区中存储了换行符。 在这两种情况下都附加了空字符 （"\0"）。

[CFile：：读取](../../mfc/reference/cfile-class.md#read)也可用于文本模式输入，但它不会在回车返回行馈送对上终止。

> [!NOTE]
> 此`CString`函数的版本将删除`'\n'`"如果存在";如果LPTSTR 版本不。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

## <a name="cstdiofileseek"></a><a name="seek"></a>CStdio文件：寻找

在以前打开的文件中重新定位指针。

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>参数

*lOff*<br/>
要移动指针的字节数。

*n 从*<br/>
指针移动模式。 必须是以下值之一：

- `CFile::begin`：从文件的开头向前移动文件指针*lOff*字节。

- `CFile::current`：从文件中的当前位置移动文件指针*lOff*字节。

- `CFile::end`：从文件末尾移动文件指针*lOff*字节。 请注意 *，lOff*必须是负的才能查找到现有文件中;正值将查找文件末尾。

### <a name="return-value"></a>返回值

如果请求的位置是合法的，则`Seek`从文件开头返回新的字节偏移量。 否则，返回值将未定义，并引发`CFileException`对象。

### <a name="remarks"></a>备注

该`Seek`函数允许通过绝对或相对地将指针移动指定数量来随机访问文件的内容。 在查找过程中实际上不会读取任何数据。 如果请求的位置大于文件的大小，文件长度将扩展到该位置，并且不会引发任何异常。

打开文件时，文件指针定位在偏移量 0，即文件的开头。

此`Seek`实现基于运行时库 （CRT） 函数`fseek`。 在文本模式下打开的`Seek`流上的用法有几个限制。 有关详细信息，请参阅[fseek，_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)。

### <a name="example"></a>示例

下面的示例演示如何使用`Seek`从`cfile`文件开头移动指针 1000 字节。 请注意，`Seek`不读取数据，因此您随后必须调用[CStdioFile：：ReadString](#readstring)读取数据。

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

## <a name="cstdiofilewritestring"></a><a name="writestring"></a>CStdio文件：写串

将数据从缓冲区写入与`CStdioFile`对象关联的文件。

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>参数

*lpsz*<br/>
指定指向包含 null 终止字符串的缓冲区的指针。

### <a name="remarks"></a>备注

终止 null 字符`\0`（ ） 不会写入文件。 此方法将*lpsz*中的换行符写入文件，作为回车换行对。

如果要将未为文件终止的数据写入文件，请使用`CStdioFile::Write`或[CFile：：：write。](../../mfc/reference/cfile-class.md#write)

如果为`CInvalidArgException*`*lpsz*参数指定 NULL，则此方法将引发 。

此方法引发 以`CFileException*`响应文件系统错误。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>另请参阅

[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[文件：:D](../../mfc/reference/cfile-class.md#duplicate)<br/>
[文件文件：锁定范围](../../mfc/reference/cfile-class.md#lockrange)<br/>
[文件文件：解锁范围](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException 类](../../mfc/reference/cnotsupportedexception-class.md)
