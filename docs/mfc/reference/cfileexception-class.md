---
title: CFileException 类
ms.date: 06/09/2020
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
ms.openlocfilehash: 85ff8d77bda30bcf0b107f733098d07c4fd80283
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813517"
---
# <a name="cfileexception-class"></a>CFileException 类

表示与文件相关的异常条件。

## <a name="syntax"></a>语法

```
class CFileException : public CException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CFileException：： CFileException](#cfileexception)|构造 `CFileException` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CFileException：： ErrnoToException](#errnotoexception)|返回与运行时错误号对应的原因代码。|
|[CFileException：： GetErrorMessage](#geterrormessage)|检索描述异常的消息。|
|[CFileException：： OsErrorToException](#oserrortoexception)|返回与操作系统错误代码相对应的原因代码。|
|[CFileException：： ThrowErrno](#throwerrno)|基于运行时错误号引发文件异常。|
|[CFileException：： ThrowOsError](#throwoserror)|基于操作系统错误号引发文件异常。|

### <a name="public-data-members"></a>公共数据成员

|“属性”|描述|
|----------|-----------------|
|[CFileException：： m_cause](#m_cause)|包含与异常原因相对应的可移植代码。|
|[CFileException：： m_lOsError](#m_loserror)|包含相关的操作系统错误号。|
|[CFileException：： m_strFileName](#m_strfilename)|包含此异常的文件的名称。|

## <a name="remarks"></a>备注

`CFileException`类包括的公共数据成员保存可移植原因代码和特定于操作系统的错误号。 类还提供静态成员函数，用于引发文件异常，并为操作系统错误和 C 运行时错误返回原因代码。

`CFileException`对象在 `CFile` 成员函数和派生类的成员函数中构造和引发。 您可以在**CATCH**表达式的作用域内访问这些对象。 对于可移植性，只使用原因代码来获取异常的原因。 有关异常的详细信息，请参阅[异常处理（MFC）](../../mfc/exception-handling-in-mfc.md)一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>要求

**标头：** afx

## <a name="cfileexceptioncfileexception"></a><a name="cfileexception"></a>CFileException：： CFileException

构造一个 `CFileException` 对象，该对象存储对象中的原因代码和操作系统代码。

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>参数

*导致*<br/>
指示异常原因的枚举类型变量。 有关可能值的列表，请参阅[CFileException：： m_cause](#m_cause) 。

*lOsError*<br/>
异常的特定于操作系统的原因（如果可用）。 *LOsError*参数提供的信息超出了*原因*。

*lpszArchiveName*<br/>
指向一个字符串，该字符串包含 `CFile` 导致异常的对象的名称。

### <a name="remarks"></a>备注

不要直接使用此构造函数，而应调用 global 函数[AfxThrowFileException](exception-processing.md#afxthrowfileexception)。

> [!NOTE]
> 变量*lOsError*仅适用于 `CFile` 和 `CStdioFile` 对象。 `CMemFile`类不处理此错误代码。

## <a name="cfileexceptionerrnotoexception"></a><a name="errnotoexception"></a>CFileException：： ErrnoToException

将给定的运行时库错误值转换为 `CFileException` 枚举的错误值。

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>参数

*nErrno*<br/>
运行时包含文件 ERRNO 中定义的整数错误代码。高.

### <a name="return-value"></a>返回值

与给定的运行时库错误值相对应的枚举值。

### <a name="remarks"></a>备注

有关可能的枚举值的列表，请参阅[CFileException：： m_cause](#m_cause) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

## <a name="cfileexceptiongeterrormessage"></a><a name="geterrormessage"></a>CFileException：： GetErrorMessage

检索描述异常的文本。

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>参数

*lpszError*<br/>
[in，out]指向接收错误消息的缓冲区的指针。

*nMaxError*<br/>
中指定缓冲区可以容纳的最大字符数。 这包括终止 null 字符。

*pnHelpContext*<br/>
[in，out]指向接收帮助上下文 ID 的无符号整数的指针。 如果 `NULL` 为，则不返回任何 ID。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果指定的缓冲区太小，则会截断错误消息。

### <a name="example"></a>示例

下面的示例使用 `CFileException::GetErrorMessage`。

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

## <a name="cfileexceptionm_cause"></a><a name="m_cause"></a>CFileException：： m_cause

包含由 `CFileException` 枚举类型定义的值。

```
int m_cause;
```

### <a name="remarks"></a>备注

此数据成员是**int**类型的公共变量。枚举器及其含义如下：

| 错误 | 值和含义 |
|--|--|
| `CFileException::none` |    0：未发生任何错误。 |
| `CFileException::genericException` |    1：发生了未指定的错误。 |
| `CFileException::fileNotFound` |    2：未能定位该文件。 |
| `CFileException::badPath` |    3：全部或部分路径无效。 |
| `CFileException::tooManyOpenFiles` |    4：已超出允许打开的文件数。 |
| `CFileException::accessDenied` |    5：无法访问该文件。 |
| `CFileException::invalidFile` |    6：已尝试使用无效的文件句柄。 |
| `CFileException::removeCurrentDir` |    7：无法移除当前工作目录。 |
| `CFileException::directoryFull` |    8：没有更多的目录项。 |
| `CFileException::badSeek` |    9：已在尝试设置文件指针时出错。 |
| `CFileException::hardIO` |    10：出现了硬件错误。 |
| `CFileException::sharingViolation` |    11：未加载 SHARE.EXE 或共享区域已被锁定。 |
| `CFileException::lockViolation` |    12：已尝试锁定已经锁定的区域。 |
| `CFileException::diskFull` | 13：磁盘已满。 |
| `CFileException::endOfFile` | 14：已到达文件结尾。 |

> [!NOTE]
> 引发这些 `CFileException` 的枚举器不同于引发 `CArchiveException` 的枚举器。

> [!NOTE]
> `CArchiveException::generic` 已弃用。 请改用 `genericException`。 如果在应用程序中使用**泛型**，并使用/clr 生成，则生成的语法错误并不容易解密。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

## <a name="cfileexceptionm_loserror"></a><a name="m_loserror"></a>CFileException：： m_lOsError

包含此异常的操作系统错误代码。

```
LONG m_lOsError;
```

### <a name="remarks"></a>备注

有关错误代码的列表，请参阅操作系统技术手册。 此数据成员是 LONG 类型的公共变量。

## <a name="cfileexceptionm_strfilename"></a><a name="m_strfilename"></a>CFileException：： m_strFileName

包含此异常条件的文件的名称。

```
CString m_strFileName;
```

## <a name="cfileexceptionoserrortoexception"></a><a name="oserrortoexception"></a>CFileException：： OsErrorToException

返回与给定的*lOsError*值相对应的枚举器。 如果错误代码未知，则函数返回 `CFileException::generic` 。

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>参数

*lOsError*<br/>
操作系统特定的错误代码。

### <a name="return-value"></a>返回值

与给定操作系统错误值相对应的枚举值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

## <a name="cfileexceptionthrowerrno"></a><a name="throwerrno"></a>CFileException：： ThrowErrno

构造 `CFileException` 对应于给定*nErrno*值的对象，然后引发异常。

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>参数

*nErrno*<br/>
运行时包含文件 ERRNO 中定义的整数错误代码。高.

*lpszFileName*<br/>
指向字符串的指针，该字符串包含引发异常的文件的名称（如果可用）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

## <a name="cfileexceptionthrowoserror"></a><a name="throwoserror"></a>CFileException：： ThrowOsError

引发 `CFileException` 对应于给定*lOsError*值的。 如果错误代码未知，则该函数将引发编码为的异常 `CFileException::generic` 。

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>参数

*lOsError*<br/>
操作系统特定的错误代码。

*lpszFileName*<br/>
指向字符串的指针，该字符串包含引发异常的文件的名称（如果可用）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>请参阅

[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[异常处理](../../mfc/reference/exception-processing.md)
