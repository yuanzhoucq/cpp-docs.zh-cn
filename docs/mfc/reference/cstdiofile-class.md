---
title: CStdioFile 类
ms.date: 11/04/2016
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
ms.openlocfilehash: dd1a13e7cef066350f8409782b0efeba11b9d11e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456207"
---
# <a name="cstdiofile-class"></a>CStdioFile 类

表示由运行时函数打开的 C 运行时流文件[fopen](../../c-runtime-library/reference/fopen-wfopen.md)。

## <a name="syntax"></a>语法

```
class CStdioFile : public CFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|构造`CStdioFile`从路径或文件指针的对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CStdioFile::Open](#open)|已重载。 打开设计用于默认值`CStdioFile`构造函数 (重写[CFile::Open](../../mfc/reference/cfile-class.md#open))。|
|[CStdioFile::ReadString](#readstring)|读取单个文本行。|
|[CStdioFile::Seek](#seek)|将当前文件指针定位。|
|[CStdioFile::WriteString](#writestring)|写入单个文本行。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|包含指向打开的文件。|

## <a name="remarks"></a>备注

Stream 文件进行缓冲，可以在文本模式 （默认值） 还是二进制模式中打开。

文本模式提供了特殊处理的回车符和换行符对。 当你编写一个换行符 (0x0A) 字符到文本模式`CStdioFile`对象、 字节对 (0x0D，0x0A) 发送到该文件。 读取时，字节对 (0x0D，0x0A) 转换为一个 0x0A 字节。

[CFile](../../mfc/reference/cfile-class.md)函数[重复](../../mfc/reference/cfile-class.md#duplicate)， [LockRange](../../mfc/reference/cfile-class.md#lockrange)，以及[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)不支持`CStdioFile`。

如果你对调用这些函数`CStdioFile`，则会[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

有关使用的详细信息`CStdioFile`，请参阅文章[MFC 中的文件](../../mfc/files-in-mfc.md)并[文件处理](../../c-runtime-library/file-handling.md)中*运行时库参考*。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="cstdiofile"></a>  CStdioFile::CStdioFile

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
指定对 C 运行时函数的调用返回的文件指针[fopen](../../c-runtime-library/reference/fopen-wfopen.md)。

*lpszFileName*<br/>
指定是所需的文件的路径的字符串。 路径可以是相对值还是绝对值。

*nOpenFlags*<br/>
指定用于创建文件、 文件共享和文件访问模式的选项。 可以使用按位 OR 来指定多个选项 ( **|** ) 运算符。

一个文件访问模式选项是必需的;其他模式是可选的。 请参阅[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)有关模式选项和其他标志的列表。 在 MFC 3.0 版及更高版本中，允许共享标志。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针。

### <a name="remarks"></a>备注

默认构造函数不会附加到一个文件`CStdioFile`对象。 在使用此构造函数，您必须使用`CStdioFile::Open`方法来打开文件并将其附加到`CStdioFile`对象。

单参数构造函数将附加到的打开的文件流`CStdioFile`对象。 允许使用指针的值包括预定义的输入/输出文件指针*stdin*， *stdout*，或*stderr*。

两个参数构造函数创建`CStdioFile`对象，并将相应的文件打开与给定的路径。

如果通过为 NULL *pOpenStream*或*lpszFileName*，构造函数引发`CInvalidArgException*`。

如果无法打开或创建文件，该构造函数将引发`CFileException*`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>  CStdioFile::m_pStream

`m_pStream`数据成员是由 C 运行时函数返回指向打开的文件的`fopen`。

```
FILE* m_pStream;
```

### <a name="remarks"></a>备注

如果从未打开该文件，或已关闭，则为 NULL。

##  <a name="open"></a>  CStdioFile::Open

已重载。 打开设计用于默认`CStdioFile`构造函数。

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
一个字符串，是所需的文件的路径。 路径可以是相对值还是绝对值。

*nOpenFlags*<br/>
共享和访问模式。 指定当打开文件时要执行的操作。 可以通过使用按位 OR 组合选项 (&#124;) 运算符。 一个访问权限和一个共享选项是必需的;modeCreate 和 modeNoInherit 模式是可选的。

*pError*<br/>
指向将接收失败的操作的状态的现有文件异常对象的指针。

*pTM*<br/>
指向 `CAtlTransactionManager` 对象的指针。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="readstring"></a>  CStdioFile::ReadString

将文本数据读入的缓冲区最大的限制*最*-1 个字符，与关联的文件从`CStdioFile`对象。

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>参数

*lpsz*<br/>
指定指向将接收的以 null 结尾的文本字符串的用户提供的缓冲区的指针。

*最*<br/>
指定要读取的字符最大数目不包括终止 null 字符。

*rString*<br/>
对引用`CString`对象，该函数返回时，将包含字符串对象。

### <a name="return-value"></a>返回值

指向包含文本数据的缓冲区的指针。 如果未读取任何数据; 已达到文件结尾，则为 NULL或者，如果布尔值，则为 FALSE 的文件结束已达到未读取任何数据。

### <a name="remarks"></a>备注

读取已停止的第一个换行符。 如果在这种情况下，少于*最*-1 字符都已读取，换行字符将存储在缓冲区。 在任一情况下将追加 null 字符 (\0)。

[CFile::Read](../../mfc/reference/cfile-class.md#read)也是可用的文本模式输入，但它不会终止回车-换行对上。

> [!NOTE]
>  `CString`此函数的版本中删除`'\n'`LPTSTR 版本不存在; 如果不会。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>  CStdioFile::Seek

在以前打开的文件指针重新定位。

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>参数

*lOff*<br/>
要将指针移动到的字节数。

*nFrom*<br/>
指针移动模式。 必须是以下值之一：

- `CFile::begin`： 将文件指针移*lOff*转发从文件开头的字节数。

- `CFile::current`： 将文件指针移*lOff*个字节从文件中的当前位置。

- `CFile::end`： 将文件指针移*lOff*从文件末尾的字节数。 请注意， *lOff*必须是负值以查找现有文件; 正值将查找文件的末尾。

### <a name="return-value"></a>返回值

如果请求的位置是合法的`Seek`从该文件的开头返回新的字节偏移量。 否则，返回值是不确定和`CFileException`引发对象。

### <a name="remarks"></a>备注

`Seek`函数允许随机访问文件的内容通过移动指针指定的量，绝对或相对。 在查找期间实际不读取任何数据。 如果请求的位置大于文件的大小，文件长度将扩展到该位置，并会引发任何异常。

当打开文件时，文件指针位于偏移量 0，该文件的开头处。

此实现`Seek`基于运行时库 (CRT) 函数`fseek`。 是有几个限制的使用情况的`Seek`上在文本模式下打开的流。 有关详细信息，请参阅[fseek、_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)。

### <a name="example"></a>示例

下面的示例演示如何使用`Seek`若要将指针移动到 1000 个字节从开头`cfile`文件。 请注意，`Seek`不会读取数据，因此你必须随后调用[CStdioFile::ReadString](#readstring)读取数据。

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>  CStdioFile::WriteString

将数据从缓冲区写入到与关联的文件`CStdioFile`对象。

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>参数

*lpsz*<br/>
指定指向包含以 null 结尾的字符串缓冲区的指针。

### <a name="remarks"></a>备注

终止 null 字符 ( `\0`) 不会写入到该文件。 此方法写入换行符*lpsz*作为回车/换行对的文件。

如果你想要写入的数据，不到文件中，使用以 null 结尾`CStdioFile::Write`或[CFile::Write](../../mfc/reference/cfile-class.md#write)。

此方法将引发`CInvalidArgException*`指定为空，如果*lpsz*参数。

此方法将引发`CFileException*`文件系统错误响应。

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
