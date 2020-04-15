---
title: 文件例外类
ms.date: 11/04/2016
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
ms.openlocfilehash: 2d1025ca33d5641982ba52f1ac539db85df3bfd5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373897"
---
# <a name="cfileexception-class"></a>文件例外类

表示与文件相关的异常条件。

## <a name="syntax"></a>语法

```
class CFileException : public CException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[文件例外：文件例外](#cfileexception)|构造 `CFileException` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[文件例外：：错误例外](#errnotoexception)|返回与运行时错误编号对应的原因代码。|
|[文件例外：获取错误消息](#geterrormessage)|检索描述异常的消息。|
|[文件例外：：错误例外](#oserrortoexception)|返回与操作系统错误代码对应的原因代码。|
|[文件例外：：ThrowErrno](#throwerrno)|根据运行时错误编号引发文件异常。|
|[文件例外：：抛掷错误](#throwoserror)|根据操作系统错误编号引发文件异常。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[文件例外：：m_cause](#m_cause)|包含与异常原因对应的可移植代码。|
|[文件例外：m_lOsError](#m_loserror)|包含相关的操作系统错误编号。|
|[文件例外：m_strFileName](#m_strfilename)|包含此异常的文件名称。|

## <a name="remarks"></a>备注

该`CFileException`类包括保存可移植原因代码和操作系统特定错误编号的公共数据成员。 该类还提供静态成员函数，用于引发文件异常，以及返回操作系统错误和 C 运行时错误的原因代码。

`CFileException`对象在源类的成员函数`CFile`和成员函数中构造和引发。 您可以在**CATCH**表达式的范围内访问这些对象。 对于可移植性，请仅使用原因代码来获取异常原因。 有关异常的详细信息，请参阅异常[处理 （MFC） 一](../../mfc/exception-handling-in-mfc.md)文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cfileexceptioncfileexception"></a><a name="cfileexception"></a>文件例外：文件例外

构造一个`CFileException`对象，该对象将原因代码和操作系统代码存储在对象中。

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>参数

*原因*<br/>
指示异常原因的枚举类型变量。 有关可能值的列表，请参阅[CFileException：：m_cause。](#m_cause)

*lOsError*<br/>
异常的特定于操作系统的原因（如果可用）。 *lOsError*参数提供的信息比*原因*多。

*lpsz存档名称*<br/>
指向包含引起异常`CFile`的对象名称的字符串。

### <a name="remarks"></a>备注

不要直接使用此构造函数，而是调用全局函数[AfxThrowFileException](exception-processing.md#afxthrowfileexception)。

> [!NOTE]
> 变量*lOsError*仅适用于`CFile`和`CStdioFile`对象。 类`CMemFile`不处理此错误代码。

## <a name="cfileexceptionerrnotoexception"></a><a name="errnotoexception"></a>文件例外：：错误例外

将给定的运行时库错误值转换为`CFileException`枚举错误值。

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>参数

*内埃尔诺*<br/>
运行时定义的整数错误代码包括文件 ERRNO。H。

### <a name="return-value"></a>返回值

对应于给定运行时库错误值的枚举值。

### <a name="remarks"></a>备注

有关可能的枚举值的列表，请参阅[CFileException：：m_cause。](#m_cause)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

## <a name="cfileexceptiongeterrormessage"></a><a name="geterrormessage"></a>文件例外：获取错误消息

检索描述异常的文本。

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>参数

*lpsz错误*<br/>
[进出]指向接收错误消息的缓冲区的指针。

*nMax错误*<br/>
[在]指定缓冲区可以保留的最大字符数。 这包括终止空字符。

*pnHelpContext*<br/>
[进出]指向接收帮助上下文 ID 的无符号整数的指针。 如果`NULL`不返回 ID。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

如果指定的缓冲区太小，错误消息将被截断。

### <a name="example"></a>示例

下面的示例使用 `CFileException::GetErrorMessage`。

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

## <a name="cfileexceptionm_cause"></a><a name="m_cause"></a>文件例外：：m_cause

包含由 `CFileException` 枚举类型定义的值。

```
int m_cause;
```

### <a name="remarks"></a>备注

此数据成员是**int**类型的公共变量。枚举器及其含义如下：

- `CFileException::none`0： 未发生错误。

- `CFileException::genericException`1： 发生未指定的错误。

- `CFileException::fileNotFound`2： 找不到该文件。

- `CFileException::badPath`3： 全部或部分路径无效。

- `CFileException::tooManyOpenFiles`4： 超过允许的打开文件数。

- `CFileException::accessDenied`5： 无法访问该文件。

- `CFileException::invalidFile`6： 有人尝试使用无效的文件句柄。

- `CFileException::removeCurrentDir`7： 无法删除当前工作目录。

- `CFileException::directoryFull`8： 没有更多的目录条目。

- `CFileException::badSeek`9： 尝试设置文件指针时出错。

- `CFileException::hardIO`10： 存在硬件错误。

- `CFileException::sharingViolation`11： 分享。EXE 未加载，或者共享区域已锁定。

- `CFileException::lockViolation`12： 有人试图锁定已锁定的区域。

- `CFileException::diskFull`14： 磁盘已满。

- `CFileException::endOfFile`15： 到达文件结尾。

    > [!NOTE]
    >  引发这些 `CFileException` 的枚举器不同于引发 `CArchiveException` 的枚举器。

    > [!NOTE]
    > `CArchiveException::generic` 已弃用。 请改用 `genericException`。 如果在应用程序中使用**泛型**并且使用 /clr 构建，则生成的语法错误不容易被破译。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

## <a name="cfileexceptionm_loserror"></a><a name="m_loserror"></a>文件例外：m_lOsError

包含此异常的操作系统错误代码。

```
LONG m_lOsError;
```

### <a name="remarks"></a>备注

有关错误代码的列表，请参阅操作系统技术手册。 此数据成员是 LONG 类型的公共变量。

## <a name="cfileexceptionm_strfilename"></a><a name="m_strfilename"></a>文件例外：m_strFileName

包含此异常条件的文件名称。

```
CString m_strFileName;
```

## <a name="cfileexceptionoserrortoexception"></a><a name="oserrortoexception"></a>文件例外：：错误例外

返回对应于给定*lOsError*值的枚举器。 如果错误代码未知，则函数将返回`CFileException::generic`。

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>参数

*lOsError*<br/>
特定于操作系统的错误代码。

### <a name="return-value"></a>返回值

对应于给定操作系统错误值的枚举值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

## <a name="cfileexceptionthrowerrno"></a><a name="throwerrno"></a>文件例外：：ThrowErrno

构造与给定`CFileException` *nErrno*值对应的对象，然后引发异常。

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>参数

*内埃尔诺*<br/>
运行时定义的整数错误代码包括文件 ERRNO。H。

*lpszFile名称*<br/>
指向包含导致异常的文件名称的文件名称的字符串的指针（如果可用）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

## <a name="cfileexceptionthrowoserror"></a><a name="throwoserror"></a>文件例外：：抛掷错误

引发`CFileException`与给定*lOsError*值对应的。 如果错误代码未知，则函数将引发一个编码为`CFileException::generic`的异常。

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>参数

*lOsError*<br/>
特定于操作系统的错误代码。

*lpszFile名称*<br/>
指向包含导致异常的文件名称的文件名称的字符串的指针（如果可用）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>另请参阅

[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[异常处理](../../mfc/reference/exception-processing.md)
