---
title: CFileException 类
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
ms.openlocfilehash: a3514c76d4136fe2bc0b096cc382e6f7f4dd3392
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205931"
---
# <a name="cfileexception-class"></a>CFileException 类

表示与文件相关的异常条件。

## <a name="syntax"></a>语法

```
class CFileException : public CException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|构造 `CFileException` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|返回导致运行时错误号相对应的代码。|
|[CFileException::GetErrorMessage](#geterrormessage)|检索描述异常的消息。|
|[CFileException::OsErrorToException](#oserrortoexception)|返回对应于操作系统错误代码的原因代码。|
|[CFileException::ThrowErrno](#throwerrno)|引发运行时错误号上基于文件异常。|
|[CFileException::ThrowOsError](#throwoserror)|引发文件异常根据操作系统错误号。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CFileException::m_cause](#m_cause)|包含与异常原因相对应的可移植代码。|
|[CFileException::m_lOsError](#m_loserror)|包含相关的操作系统错误号。|
|[CFileException::m_strFileName](#m_strfilename)|包含此异常的文件的名称。|

## <a name="remarks"></a>备注

`CFileException`类包含保存的可移植的原因代码和特定于操作系统的错误号的公共数据成员。 此类还提供静态成员函数引发文件异常和返回操作系统错误和 C 运行时错误的原因代码。

`CFileException` 对象是构造，引发`CFile`成员函数在派生类的成员函数。 您可以访问这些对象的作用域内**捕获**表达式。 可移植性，使用仅原因代码以获取异常的原因。 有关异常的详细信息，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="cfileexception"></a>  CFileException::CFileException

构造`CFileException`对象中存储的原因代码和操作系统代码的对象。

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>参数

*cause*<br/>
指示异常原因的枚举的类型变量。 请参阅[CFileException::m_cause](#m_cause)有关的可能值列表。

*lOsError*<br/>
异常，如果有一个特定于操作系统的原因。 *LOsError*参数提供的信息多于*导致*does。

*lpszArchiveName*<br/>
指向包含名称的字符串`CFile`导致发生异常的对象。

### <a name="remarks"></a>备注

请勿直接，使用此构造函数而不是调用全局函数[AfxThrowFileException](exception-processing.md#afxthrowfileexception)。

> [!NOTE]
>  在变量*lOsError*仅适用于`CFile`和`CStdioFile`对象。 `CMemFile`类不处理此错误代码。

##  <a name="errnotoexception"></a>  CFileException::ErrnoToException

将给定的运行时库的错误值到转换`CFileException`枚举错误值。

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>参数

*nErrno*<br/>
在运行时包含文件 ERRNO 中定义一个整数错误代码。H.

### <a name="return-value"></a>返回值

为给定的运行时库的错误值相对应的枚举的值。

### <a name="remarks"></a>备注

请参阅[CFileException::m_cause](#m_cause)有关一系列可能的枚举值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

##  <a name="geterrormessage"></a>  CFileException::GetErrorMessage

检索描述异常的文本。

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>参数

*lpszError*<br/>
[in、 out]指向接收一条错误消息的缓冲区。

*nMaxError*<br/>
[in]最大可以容纳指定的缓冲区的字符数。 这包括终止 null 字符。

*pnHelpContext*<br/>
[in、 out]为接收帮助上下文 id。 无符号整数的指针 如果`NULL`，返回没有 ID。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

如果指定的缓冲区太小，错误消息将被截断。

### <a name="example"></a>示例

下面的示例使用`CFileException::GetErrorMessage`。

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

##  <a name="m_cause"></a>  CFileException::m_cause

包含由 `CFileException` 枚举类型定义的值。

```
int m_cause;
```

### <a name="remarks"></a>备注

此数据成员是类型的公共变量**int**。枚举器及其含义如下所示：

- `CFileException::none` 0:未发生错误。

- `CFileException::genericException` 1:发生了未指定的错误。

- `CFileException::fileNotFound` 2:找不到文件。

- `CFileException::badPath` 3:全部或部分路径无效。

- `CFileException::tooManyOpenFiles` 4:超出了允许的打开的文件数。

- `CFileException::accessDenied` 5:无法访问该文件。

- `CFileException::invalidFile` 6:试图使用无效的文件句柄。

- `CFileException::removeCurrentDir` 7:不能删除当前工作目录。

- `CFileException::directoryFull` 8:没有更多的目录条目。

- `CFileException::badSeek` 9:尝试设置文件指针时出错。

- `CFileException::hardIO` 10:出现硬件错误。

- `CFileException::sharingViolation` 11:共享。未加载 EXE，或共享的区域被锁定。

- `CFileException::lockViolation` 12:尝试锁定已被锁定的区域时出现。

- `CFileException::diskFull` 14:磁盘已满。

- `CFileException::endOfFile` 15:已达到文件结尾。

    > [!NOTE]
    >  引发这些 `CFileException` 的枚举器不同于引发 `CArchiveException` 的枚举器。

    > [!NOTE]
    > `CArchiveException::generic` 已弃用。 请改用 `genericException`。 如果**泛型**是应用程序中使用和构建用 /clr 生成，则生成的语法错误并不容易解密。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

##  <a name="m_loserror"></a>  CFileException::m_lOsError

包含此异常的操作系统错误代码。

```
LONG m_lOsError;
```

### <a name="remarks"></a>备注

请参阅你操作系统技术手册，错误代码的列表。 此数据成员是公共类型的变量的长时间。

##  <a name="m_strfilename"></a>  CFileException::m_strFileName

包含此异常条件的文件的名称。

```
CString m_strFileName;
```

##  <a name="oserrortoexception"></a>  CFileException::OsErrorToException

返回一个枚举器对应于给定*lOsError*值。 如果错误代码为未知，则该函数将返回`CFileException::generic`。

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>参数

*lOsError*<br/>
特定于操作系统的错误代码。

### <a name="return-value"></a>返回值

枚举的值，对应于给定的操作系统错误值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

##  <a name="throwerrno"></a>  CFileException::ThrowErrno

构造`CFileException`对象对应于给定*nErrno*值，然后引发异常。

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>参数

*nErrno*<br/>
在运行时包含文件 ERRNO 中定义一个整数错误代码。H.

*lpszFileName*<br/>
如果有指向包含的文件的名称的字符串的指针导致异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

##  <a name="throwoserror"></a>  CFileException::ThrowOsError

将引发`CFileException`对应于给定*lOsError*值。 如果错误代码为未知，则该函数将引发异常的编码与`CFileException::generic`。

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>参数

*lOsError*<br/>
特定于操作系统的错误代码。

*lpszFileName*<br/>
如果有指向包含的文件的名称的字符串的指针导致异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>请参阅

[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[异常处理](../../mfc/reference/exception-processing.md)
