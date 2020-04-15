---
title: 异常处理
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
ms.openlocfilehash: d819c170f47ea259e776bce6db0a6971e3f54bec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365719"
---
# <a name="exception-processing"></a>异常处理

当程序执行时，可能会出现许多称为"异常"的异常条件和错误。 这些可能包括内存不足、资源分配错误和找不到文件。

Microsoft 基础类库使用一种异常处理方案，该方案与 ANSI 标准委员会提出的C++方案紧密建模。 在调用可能遇到异常情况的函数之前，必须设置异常处理程序。 如果函数遇到异常情况，它将引发异常，并将控件传递给异常处理程序。

Microsoft 基础类库中包含的几个宏将设置异常处理程序。 许多其他全局函数有助于引发专用异常并在必要时终止程序。 这些宏和全局函数分为以下几类：

- 异常宏，它构造异常处理程序。

- 异常引发函数），生成特定类型的异常。

- 终止函数，导致程序终止。

有关示例和更多详细信息，请参阅文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="exception-macros"></a>异常宏

|||
|-|-|
|[TRY](#try)|指定用于异常处理的代码块。|
|[抓住](#catch)|指定一个代码块，用于从前面的**TRY**块捕获异常。|
|[CATCH_ALL](#catch_all)|指定一个代码块，用于捕获前面**TRY**块中的所有异常。|
|[AND_CATCH](#and_catch)|指定一个代码块，用于从前面的**TRY**块捕获其他异常类型。|
|[AND_CATCH_ALL](#and_catch_all)|指定一个代码块，用于捕获前面**TRY**块中引发的任何其他异常类型。|
|[END_CATCH](#end_catch)|结束最后一个**CATCH**或**AND_CATCH**代码块。|
|[END_CATCH_ALL](#end_catch_all)|结束最后**一个CATCH_ALL**代码块。|
|[扔](#throw)|引发指定的异常。|
|[THROW_LAST](#throw_last)|将当前处理的异常引发到下一个外部处理程序。|

### <a name="exception-throwing-functions"></a>异常引发函数

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|引发存档异常。|
|[AfxThrowFileException](#afxthrowfileexception)|引发文件异常。|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|引发无效参数异常。|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|引发内存异常。|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|引发不支持的异常。|
|[AfxThrowResourceException](#afxthrowresourceexception)|引发未找到的 Windows 资源异常。|
|[AfxThrowUserException](#afxthrowuserexception)|在用户启动的程序操作中引发异常。|

MFC 提供两个专门针对 OLE 异常的异常引发功能：

### <a name="ole-exception-functions"></a>OLE 异常函数

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|在 OLE 自动化功能中引发异常。|
|[AfxThrowOleException](#afxthrowoleexception)|引发 OLE 异常。|

为了支持数据库异常，数据库类提供了两个异常类和`CDBException``CDaoException`和 和全局函数来支持异常类型：

### <a name="dao-exception-functions"></a>DAO 异常函数

|||
|-|-|
|[阿不都·阿不都拉多例外](#afxthrowdaoexception)|从您自己的代码中抛出一个[CDaoException。](../../mfc/reference/cdaoexception-class.md)|
|[AfxThrowDBException](#afxthrowdbexception)|从您自己的代码中引发[CDBException。](../../mfc/reference/cdbexception-class.md)|

MFC 提供以下终止功能：

### <a name="termination-functions"></a>终止功能

|||
|-|-|
|[AfxAbort](#afxabort)|调用以在发生致命错误时终止应用程序。|

## <a name="try"></a><a name="try"></a>尝试

设置**TRY**块。

```
TRY
```

### <a name="remarks"></a>备注

**TRY**块标识可能会引发异常的代码块。 这些异常在以下**CATCH**和**AND_CATCH**块中处理。 允许递归：异常可以通过忽略它们或使用THROW_LAST宏传递给外部**TRY**块。 使用END_CATCH或END_CATCH_ALL宏结束**TRY**块。

有关详细信息，请参阅文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="example"></a>示例

请参阅[CATCH](#catch)的示例。

### <a name="requirements"></a>要求

标头：afx.h

## <a name="catch"></a><a name="catch"></a>抓住

定义捕获前面**TRY**块中引发的第一个异常类型的代码块。

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_class*<br/>
指定要测试的异常类型。 有关标准异常类的列表，请参阅类[Cexception](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
为将由宏创建的异常对象指针指定名称。 可以使用指针名称访问**CATCH**块中的异常对象。 已为您声明此变量。

### <a name="remarks"></a>备注

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用THROW_LAST宏以将处理转移到下一个外部异常帧。 使用END_CATCH宏结束**TRY**块。

如果*exception_class*是类`CException`，则将捕获所有异常类型。 您可以使用[CObject：IsKindOf](../../mfc/reference/cobject-class.md#iskindof)成员函数来确定引发的特定异常。 捕获多种异常的更好方法是使用顺序**AND_CATCH**语句，每种语句都具有不同的异常类型。

异常对象指针由宏创建。 你不需要自己声明它。

> [!NOTE]
> **CATCH**块定义为由大括号划定的C++作用域。 如果您在此范围中声明变量，则只能在该范围中访问它们。 这也适用于*exception_object_pointer_name。*

有关异常和 CATCH 宏的详细信息，请参阅文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

## <a name="catch_all"></a><a name="catch_all"></a>CATCH_ALL

定义捕获前面**TRY**块中引发的所有异常类型的代码块。

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_object_pointer_name*<br/>
为将由宏创建的异常对象指针指定名称。 您可以使用指针名访问 `CATCH_ALL` 块中的异常对象。 已为您声明此变量。

### <a name="remarks"></a>备注

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用 `THROW_LAST` 宏以将处理移动到下一个外部异常帧。 如果使用**CATCH_ALL**，请用END_CATCH_ALL宏结束**TRY**块。

> [!NOTE]
> **CATCH_ALL**块定义为由大括号划定的C++作用域。 如果您在此范围中声明变量，则只能在该范围中访问它们。

有关异常的详细信息，请参阅文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="example"></a>示例

请参阅[CFile 的示例：：中止](../../mfc/reference/cfile-class.md#abort)。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="and_catch"></a><a name="and_catch"></a>AND_CATCH

定义代码块，用于捕获在前面的**TRY**块中引发的其他异常类型。

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_class*<br/>
指定要测试的异常类型。 有关标准异常类的列表，请参阅类[Cexception](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
由宏创建的异常对象指针的名称。 可以使用指针名称访问**AND_CATCH**块中的异常对象。 已为您声明此变量。

### <a name="remarks"></a>备注

使用 CATCH 宏捕获一种异常类型，然后AND_CATCH宏捕获每个后续类型。 使用END_CATCH宏结束**TRY**块。

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用**AND_CATCH**块中的THROW_LAST宏，将处理转移到下一个外部异常帧。 **AND_CATCH**标记前一个**CATCH**或**AND_CATCH**块的末尾。

> [!NOTE]
> **AND_CATCH**块定义为C++范围（由大括号定义）。 如果在此作用域中声明变量，请记住它们只能在该作用域内访问。 这也适用于*exception_object_pointer_name*变量。

### <a name="example"></a>示例

请参阅[CATCH](#catch)的示例。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="and_catch_all"></a><a name="and_catch_all"></a>AND_CATCH_ALL

定义代码块，用于捕获在前面的**TRY**块中引发的其他异常类型。

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_object_pointer_name*<br/>
由宏创建的异常对象指针的名称。 可以使用指针名称访问**AND_CATCH_ALL**块中的异常对象。 已为您声明此变量。

### <a name="remarks"></a>备注

使用**CATCH**宏捕获一种异常类型，然后AND_CATCH_ALL宏捕获所有其他后续类型。 如果使用AND_CATCH_ALL，请用END_CATCH_ALL宏结束**TRY**块。

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用**AND_CATCH_ALL**块中的THROW_LAST宏以将处理转移到下一个外部异常帧。 **AND_CATCH_ALL**标记前一个**CATCH**或**AND_CATCH_ALL**块的末尾。

> [!NOTE]
> **AND_CATCH_ALL**块定义为C++范围（由大括号定义）。 如果在此作用域中声明变量，请记住它们只能在该作用域内访问。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="end_catch"></a><a name="end_catch"></a>END_CATCH

标记最后一个**CATCH**或**AND_CATCH**块的末尾。

```
END_CATCH
```

### <a name="remarks"></a>备注

有关END_CATCH宏的详细信息，请参阅文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="end_catch_all"></a><a name="end_catch_all"></a>END_CATCH_ALL

标记最后一**个CATCH_ALL88**或**AND_CATCH_ALL**块的结束。

```
END_CATCH_ALL
```

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="throw-mfc"></a><a name="throw"></a>THROW （MFC）

引发指定的异常。

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>参数

*exception_object_pointer*<br/>
指向派生自`CException`的异常对象。

### <a name="remarks"></a>备注

**THROW**中断程序执行，将控制权传递到程序中的关联**CATCH**块。 如果尚未提供**CATCH**块，则控件将传递给 Microsoft 基础类库模块，该模块打印错误消息并退出。

有关详细信息，请参阅文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="throw_last"></a><a name="throw_last"></a>THROW_LAST

将异常扔回下一个外部**CATCH**块。

```
THROW_LAST()
```

### <a name="remarks"></a>备注

此宏允许您引发本地创建的异常。 如果您尝试引发刚刚捕获的异常，它通常会超出范围并被删除。 对于**THROW_LAST**，异常将正确传递给下一个**CATCH**处理程序。

有关详细信息，请参阅文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="example"></a>示例

请参阅[CFile 的示例：：中止](../../mfc/reference/cfile-class.md#abort)。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="afxthrowarchiveexception"></a><a name="afxthrowarchiveexception"></a>AfxThrow存档例外

引发存档异常。

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>参数

*原因*<br/>
指定指示异常原因的整数。 有关可能值的列表，请参阅[CArchiveException：：：m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)。

*lpsz存档名称*<br/>
指向包含导致异常`CArchive`的对象的名称的字符串（如果可用）。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="afxthrowfileexception"></a><a name="afxthrowfileexception"></a>AfxThrow文件例外

引发文件异常。

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>参数

*原因*<br/>
指定指示异常原因的整数。 有关可能值的列表，请参阅[CFileException：：：m_cause](../../mfc/reference/cfileexception-class.md#m_cause)。

*lOsError*<br/>
包含说明异常原因的操作系统错误编号（如果可用）。 有关错误代码的列表，请参阅操作系统手册。

*lpszFile名称*<br/>
指向包含导致异常的文件名称的文件名称的字符串（如果可用）。

### <a name="remarks"></a>备注

您负责根据操作系统错误代码确定原因。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="afxthrowinvalidargexception"></a><a name="afxthrowinvalidargexception"></a>AfxThrow 无效异常

引发无效参数异常。

### <a name="syntax"></a>语法

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>备注

使用无效参数时调用此函数。

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxthrowmemoryexception"></a><a name="afxthrowmemoryexception"></a>AfxThrow 记忆异常

引发内存异常。

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>备注

如果对基础系统内存分配器（如**malloc**和[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows 函数）的调用失败，请调用此功能。 您无需调用它**作为新**，因为如果内存分配失败 **，new**将自动引发内存异常。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="afxthrownotsupportedexception"></a><a name="afxthrownotsupportedexception"></a>AfxThrow 不支持例外

引发由请求不支持的功能的结果的异常。

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="afxthrowresourceexception"></a><a name="afxthrowresourceexception"></a>AfxThrow 资源异常

引发资源异常。

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>备注

当无法加载 Windows 资源时，通常会调用此功能。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="afxthrowuserexception"></a><a name="afxthrowuserexception"></a>AfxThrowUser 例外

引发异常以停止最终用户操作。

```
void AfxThrowUserException();
```

### <a name="remarks"></a>备注

通常在向用户报告错误后立即`AfxMessageBox`调用此功能。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="afxthrowoledispatchexception"></a><a name="afxthrowoledispatchexception"></a>AfxThrowOle调度异常

使用此函数将在 OLE 自动化函数中引发异常。

```
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,
    LPCSTR lpszDescription,
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,
    UINT nDescriptionID,
    UINT nHelpID = -1);
```

### <a name="parameters"></a>参数

*w代码*<br/>
特定于应用程序的错误代码。

*lpsz描述*<br/>
错误的文字说明。

*n 描述ID*<br/>
错误文字说明的资源 ID。

*nHelpID*<br/>
应用程序的帮助 (.HLP) 文件的帮助上下文。

### <a name="remarks"></a>备注

提供给此函数的信息可由驱动应用程序（Microsoft Visual Basic 或其他 OLE 自动化客户端应用程序）显示。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="afxthrowoleexception"></a><a name="afxthrowoleexception"></a>阿不都·阿不都列索

创建类型`COleException`对象并引发异常。

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>参数

*Sc*<br/>
指示异常原因的 OLE 状态代码。

*人力资源*<br/>
处理指示异常原因的结果代码。

### <a name="remarks"></a>备注

将 HRESULT 作为参数的版本将结果代码转换为相应的 SCODE。 有关 HRESULT 和 SCODE 的详细信息，请参阅 Windows SDK 中的[COM 错误代码结构](/windows/win32/com/structure-of-com-error-codes)。

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="afxthrowdaoexception"></a><a name="afxthrowdaoexception"></a>阿fxThrowDao例外

调用此函数从您自己的代码中引发[CDaoException](../../mfc/reference/cdaoexception-class.md)类型的异常。

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>参数

*nAfxDao错误*<br/>
表示 DAO 扩展错误代码的整数值，可以是[CDaoException：：：m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)下列出的值之一。

*scode*<br/>
来自 DAO 的 OLE 错误代码，类型为 SCODE。 有关详细信息，请参阅[CDaoexception：：m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)。

### <a name="remarks"></a>备注

框架也称为`AfxThrowDaoException`。 在呼叫中，您可以传递其中一个参数或两者。 例如，如果要引发**CDaoException：：nAfxDaoError**中定义的错误之一，但您不关心*scode*参数，请通过*nAfxDaoError*参数中的有效代码，并接受*scode*的默认值。

有关与 MFC DAO 类相关的异常的信息，请参阅本书`CDaoException`中的类和文章["例外：数据库例外](../../mfc/exceptions-database-exceptions.md)"。

### <a name="requirements"></a>要求

  **头**afxdb.h

## <a name="afxthrowdbexception"></a><a name="afxthrowdbexception"></a>AfxThrowDB例外

调用此函数从您自己的代码中引发类型`CDBException`异常。

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>参数

*nRetCode*<br/>
类型 RETCODE 的值，用于定义导致引发异常的错误类型。

*Pdb*<br/>
指向表示与异常`CDatabase`关联的数据源连接的对象的指针。

*hstmt*<br/>
指定与异常关联的语句句柄的 ODBC HSTMT 句柄。

### <a name="remarks"></a>备注

当从调用`AfxThrowDBException`ODBC API 函数收到 ODBC RETCODE 时，该框架会调用该框架，并将 RETCODE 解释为特殊条件，而不是预期错误。 例如，数据访问操作可能会由于磁盘读取错误而失败。

有关 ODBC 定义的 RETCODE 值的信息，请参阅 Windows SDK 中的第 8 章"检索状态和错误信息"。 有关 MFC 扩展到这些代码的信息，请参阅类[CDBException](../../mfc/reference/cdbexception-class.md)。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="afxabort"></a><a name="afxabort"></a>阿fxAbort

MFC 提供的默认终止功能。

```
void  AfxAbort();
```

### <a name="remarks"></a>备注

`AfxAbort`当出现致命错误（如无法处理的未捕获异常）时，MFC 成员函数将在内部调用。 当您遇到无法`AfxAbort`恢复的灾难性错误时，可以在极少数情况下调用。

### <a name="example"></a>示例

请参阅[CATCH](#catch)的示例。

### <a name="requirements"></a>要求

  **标题**afx.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](mfc-macros-and-globals.md)<br/>
[CException 类](cexception-class.md)<br/>
[CInvalidArgException 类](cinvalidargexception-class.md)
