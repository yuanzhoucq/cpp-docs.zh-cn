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
ms.openlocfilehash: 337fe03ab09a6ed3da283f45dd4eb58aaaad5bc5
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957505"
---
# <a name="exception-processing"></a>异常处理

当程序执行时, 会出现一些异常情况和称为 "异常" 的错误。 其中可能包括内存不足、资源分配错误和查找文件失败。

Microsoft 基础类库使用异常处理方案, 该方案与的 ANSI 标准委员会所建议的方法密切建模C++。 在调用可能会遇到异常情况的函数之前, 必须设置异常处理程序。 如果函数遇到异常情况, 则会引发异常, 并将控制传递给异常处理程序。

Microsoft 基础类库中附带的多个宏将设置异常处理程序。 如果需要, 其他一些全局函数有助于引发专用异常和终止程序。 这些宏和全局函数分为以下几类:

- 异常宏, 用于构造异常处理程序。

- 异常引发函数), 该函数生成特定类型的异常。

- 终止函数, 这会导致程序终止。

有关示例和详细信息, 请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="exception-macros"></a>异常宏

|||
|-|-|
|[然后](#try)|指定用于异常处理的代码块。|
|[CATCH](#catch)|指定一个代码块, 用于捕获前面的**TRY**块中的异常。|
|[CATCH_ALL](#catch_all)|指定一个代码块, 用于捕获前面的**TRY**块中的所有异常。|
|[AND_CATCH](#and_catch)|指定一个代码块, 用于捕获前面的**TRY**块中的其他异常类型。|
|[AND_CATCH_ALL](#and_catch_all)|指定一个代码块, 用于捕获前面的**TRY**块中引发的所有其他其他异常类型。|
|[END_CATCH](#end_catch)|结束最后一个**CATCH**或**AND_CATCH**代码块。|
|[END_CATCH_ALL](#end_catch_all)|结束最后一个**CATCH_ALL**代码块。|
|[放弃](#throw)|引发指定的异常。|
|[THROW_LAST](#throw_last)|将当前处理的异常引发到下一个外部处理程序。|

### <a name="exception-throwing-functions"></a>异常引发函数

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|引发存档异常。|
|[AfxThrowFileException](#afxthrowfileexception)|引发文件异常。|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|引发无效的参数异常。|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|引发内存异常。|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|引发不受支持的异常。|
|[AfxThrowResourceException](#afxthrowresourceexception)|引发 "未找到 Windows 资源" 异常。|
|[AfxThrowUserException](#afxthrowuserexception)|在用户启动的程序操作中引发异常。|

MFC 针对 OLE 异常提供了两个异常引发函数:

### <a name="ole-exception-functions"></a>OLE 异常函数

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|在 OLE 自动化函数内引发异常。|
|[AfxThrowOleException](#afxthrowoleexception)|引发 OLE 异常。|

为了支持数据库异常, 数据库类提供了两个异常类`CDBException`和`CDaoException`全局函数来支持异常类型:

### <a name="dao-exception-functions"></a>DAO 异常函数

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|从自己的代码中引发[CDaoException](../../mfc/reference/cdaoexception-class.md) 。|
|[AfxThrowDBException](#afxthrowdbexception)|从自己的代码中引发[CDBException](../../mfc/reference/cdbexception-class.md) 。|

MFC 提供以下终止函数:

### <a name="termination-functions"></a>终止函数

|||
|-|-|
|[AfxAbort](#afxabort)|调用以在发生致命错误时终止应用程序。|

##  <a name="try"></a>然后

设置**TRY**块。

```
TRY
```

### <a name="remarks"></a>备注

**TRY**块标识可能引发异常的代码块。 在以下**CATCH**和**AND_CATCH**块中处理这些异常。 允许递归: 异常可以通过忽略它们或使用 THROW_LAST 宏传递到外部**TRY**块。 使用 END_CATCH 或 END_CATCH_ALL 宏结束**TRY**块。

有关详细信息, 请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>示例

请参阅[CATCH](#catch)的示例。

### <a name="requirements"></a>要求

标头：afx.h

##  <a name="catch"></a>  CATCH

定义一个代码块, 该代码块捕获前面的**TRY**块中引发的第一个异常类型。

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_class*<br/>
指定要测试的异常类型。 有关标准异常类的列表, 请参阅类[CException](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
为将由宏创建的异常对象指针指定名称。 使用指针名称可以访问**CATCH**块中的异常对象。 已为您声明此变量。

### <a name="remarks"></a>备注

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用 THROW_LAST 宏以将处理移动到下一个外部异常帧。 用 END_CATCH 宏结束**TRY**块。

如果*exception_class*是类`CException`, 则会捕获所有异常类型。 您可以使用[CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)成员函数确定引发的特定异常。 捕获几种异常的更好方法是使用顺序**AND_CATCH**语句, 每个语句都有不同的异常类型。

异常对象指针是由宏创建的。 无需自行声明。

> [!NOTE]
>  **CATCH**块定义为由大括号C++分隔的作用域。 如果您在此范围中声明变量，则只能在该范围中访问它们。 这也适用于*exception_object_pointer_name*。

有关异常和 CATCH 宏的详细信息, 请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>  CATCH_ALL

定义一段代码, 该代码块捕获前面的**TRY**块中引发的所有异常类型。

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_object_pointer_name*<br/>
为将由宏创建的异常对象指针指定名称。 您可以使用指针名访问 `CATCH_ALL` 块中的异常对象。 已为您声明此变量。

### <a name="remarks"></a>备注

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用 `THROW_LAST` 宏以将处理移动到下一个外部异常帧。 如果使用**CATCH_ALL**, 请使用 END_CATCH_ALL 宏结束**TRY**块。

> [!NOTE]
>  **CATCH_ALL**块定义为由大括号C++分隔的作用域。 如果您在此范围中声明变量，则只能在该范围中访问它们。

有关异常的详细信息, 请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>示例

请参阅[CFile:: Abort](../../mfc/reference/cfile-class.md#abort)的示例。

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="and_catch"></a>AND_CATCH

定义一个代码块, 用于捕获前面的**TRY**块中引发的其他异常类型。

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_class*<br/>
指定要测试的异常类型。 有关标准异常类的列表, 请参阅类[CException](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
将由宏创建的异常对象指针的名称。 您可以使用指针名称访问**AND_CATCH**块中的 exception 对象。 已为您声明此变量。

### <a name="remarks"></a>备注

使用 CATCH 宏捕获一个异常类型, 然后使用 AND_CATCH 宏捕获每个后续类型。 用 END_CATCH 宏结束**TRY**块。

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 在**AND_CATCH**块中调用 THROW_LAST 宏, 将处理转移到下一个外部异常帧。 **AND_CATCH**标记前面**CATCH**或**AND_CATCH**块的结尾。

> [!NOTE]
>  **AND_CATCH**块定义为一个C++作用域 (由大括号分隔)。 如果在此范围中声明变量, 请记住它们只能在该范围内访问。 这也适用于*exception_object_pointer_name*变量。

### <a name="example"></a>示例

请参阅[CATCH](#catch)的示例。

### <a name="requirements"></a>要求

  **标头**afx
##  <a name="and_catch_all"></a>  AND_CATCH_ALL

定义一个代码块, 用于捕获前面的**TRY**块中引发的其他异常类型。

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_object_pointer_name*<br/>
将由宏创建的异常对象指针的名称。 您可以使用指针名称访问**AND_CATCH_ALL**块中的 exception 对象。 已为您声明此变量。

### <a name="remarks"></a>备注

使用**catch**宏捕获一个异常类型, 然后使用 AND_CATCH_ALL 宏捕获所有其他后续类型。 如果使用 AND_CATCH_ALL, 请使用 END_CATCH_ALL 宏结束**TRY**块。

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 在**AND_CATCH_ALL**块中调用 THROW_LAST 宏, 将处理转移到下一个外部异常帧。 **AND_CATCH_ALL**标记前面**CATCH**或**AND_CATCH_ALL**块的结尾。

> [!NOTE]
>  **AND_CATCH_ALL**块定义为C++范围 (用大括号分隔)。 如果在此范围中声明变量, 请记住它们只能在该范围内访问。

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="end_catch"></a>END_CATCH

标记最后一个**CATCH**或**AND_CATCH**块的结尾。

```
END_CATCH
```

### <a name="remarks"></a>备注

有关 END_CATCH 宏的详细信息, 请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="end_catch_all"></a>END_CATCH_ALL

标记上一个**CATCH_ALL88**或**AND_CATCH_ALL**块的结尾。

```
END_CATCH_ALL
```

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="throw"></a>THROW (MFC)

引发指定的异常。

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>参数

*exception_object_pointer*<br/>
指向派生自`CException`的异常对象。

### <a name="remarks"></a>备注

**引发**中断程序的执行, 并将控制权传递给程序中的关联**CATCH**块。 如果尚未提供**CATCH**块, 则会将控制传递给打印错误消息并退出的 Microsoft 基础类库模块。

有关详细信息, 请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="throw_last"></a>  THROW_LAST

向下一个外部**CATCH**块引发异常。

```
THROW_LAST()
```

### <a name="remarks"></a>备注

此宏允许引发本地创建的异常。 如果尝试引发刚捕获的异常, 则通常会超出范围并将其删除。 对于**THROW_LAST**, 异常将正确传递到下一个**CATCH**处理程序。

有关详细信息, 请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>示例

请参阅[CFile:: Abort](../../mfc/reference/cfile-class.md#abort)的示例。

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="afxthrowarchiveexception"></a>  AfxThrowArchiveException

引发存档异常。

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>参数

*cause*<br/>
指定一个整数, 该整数指示异常的原因。 有关可能值的列表, 请参阅[CArchiveException:: m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)。

*lpszArchiveName*<br/>
指向包含引发异常的`CArchive`对象的名称的字符串 (如果可用)。

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="afxthrowfileexception"></a>  AfxThrowFileException

引发文件异常。

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>参数

*cause*<br/>
指定一个整数, 该整数指示异常的原因。 有关可能值的列表, 请参阅[CFileException:: m_cause](../../mfc/reference/cfileexception-class.md#m_cause)。

*lOsError*<br/>
包含说明异常原因的操作系统错误号 (如果可用)。 有关错误代码的列表, 请参阅操作系统手册。

*lpszFileName*<br/>
指向一个字符串, 该字符串包含导致异常的文件的名称 (如果可用)。

### <a name="remarks"></a>备注

你负责根据操作系统错误代码确定原因。

### <a name="requirements"></a>要求

  **标头**afx

## <a name="afxthrowinvalidargexception"></a>  AfxThrowInvalidArgException

引发无效的参数异常。

### <a name="syntax"></a>语法

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>备注

使用无效参数时将调用此函数。

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxthrowmemoryexception"></a>  AfxThrowMemoryException

引发内存异常。

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>备注

如果对基础系统内存分配器 (如**malloc**和[GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) Windows 函数) 的调用失败, 请调用此函数。 不需要为**new**调用该方法, 因为如果内存分配失败, 则**new**将自动引发内存异常。

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="afxthrownotsupportedexception"></a>  AfxThrowNotSupportedException

引发一个异常, 该异常是对不受支持的功能的请求的结果。

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="afxthrowresourceexception"></a>  AfxThrowResourceException

引发资源异常。

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>备注

当无法加载 Windows 资源时, 通常会调用此函数。

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="afxthrowuserexception"></a>  AfxThrowUserException

引发异常以停止最终用户操作。

```
void AfxThrowUserException();
```

### <a name="remarks"></a>备注

通常, 在向用户报告错误`AfxMessageBox`后立即调用此函数。

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchException

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

*wCode*<br/>
特定于应用程序的错误代码。

*lpszDescription*<br/>
错误的文字说明。

*nDescriptionID*<br/>
错误文字说明的资源 ID。

*nHelpID*<br/>
应用程序的帮助 (.HLP) 文件的帮助上下文。

### <a name="remarks"></a>备注

提供给此函数的信息可由驱动应用程序（Microsoft Visual Basic 或其他 OLE 自动化客户端应用程序）显示。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="afxthrowoleexception"></a>  AfxThrowOleException

创建类型`COleException`为的对象, 并引发异常。

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>参数

*sc*<br/>
指示异常原因的 OLE 状态代码。

*hr*<br/>
指示异常原因的结果代码的句柄。

### <a name="remarks"></a>备注

采用 HRESULT 作为参数的版本将该结果代码转换为相应的 SCODE。 有关 HRESULT 和 SCODE 的详细信息, 请参阅 Windows SDK 中[COM 错误代码的结构](/windows/desktop/com/structure-of-com-error-codes)。

### <a name="requirements"></a>要求

  **标头**afxdao

##  <a name="afxthrowdaoexception"></a>  AfxThrowDaoException

调用此函数可从自己的代码中引发类型为[CDaoException](../../mfc/reference/cdaoexception-class.md)的异常。

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>参数

*nAfxDaoError*<br/>
一个整数值, 表示 DAO 扩展错误代码, 可以是[CDaoException:: m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)下列出的值之一。

*scode*<br/>
DAO 类型为 SCODE 的 OLE 错误代码。 有关信息, 请参阅[CDaoException:: m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)。

### <a name="remarks"></a>备注

框架还会调用`AfxThrowDaoException`。 在调用中, 可以传递其中一个参数或同时传递两者。 例如, 如果要引发**CDaoException:: nAfxDaoError**中定义的错误之一, 但不关心*scode*参数, 请在*nAfxDaoError*参数中传递有效的代码, 并接受*scode*的默认值。

有关与 MFC DAO 类相关的异常的信息, 请参阅`CDaoException`本书中的类和以下[文章:数据库异常](../../mfc/exceptions-database-exceptions.md)。

### <a name="requirements"></a>要求

  **标头**afxdb

##  <a name="afxthrowdbexception"></a>  AfxThrowDBException

调用此函数可从自己的代码中`CDBException`引发类型的异常。

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>参数

*nRetCode*<br/>
RETCODE 类型的值, 用于定义导致引发异常的错误类型。

*pdb*<br/>
指向`CDatabase`对象的指针, 该对象表示与异常相关联的数据源连接。

*hstmt*<br/>
ODBC HSTMT 句柄, 用于指定与异常相关联的语句句柄。

### <a name="remarks"></a>备注

框架在从`AfxThrowDBException`对 odbc API 函数的调用接收 odbc RETCODE 时调用, 并将 RETCODE 解释为异常条件, 而不是 expectable 错误。 例如, 由于磁盘读取错误, 数据访问操作可能会失败。

有关 ODBC 定义的 RETCODE 值的信息, 请参阅 Windows SDK 中的第8章 "检索状态和错误信息"。 有关这些代码的 MFC 扩展的信息, 请参阅类[CDBException](../../mfc/reference/cdbexception-class.md)。

### <a name="requirements"></a>要求

  **标头**afx

##  <a name="afxabort"></a>AfxAbort

MFC 提供的默认终止函数。

```
void  AfxAbort();
```

### <a name="remarks"></a>备注

`AfxAbort`出现错误时, 由 MFC 成员函数在内部调用, 如无法处理的未捕获的异常。 如果遇到无法`AfxAbort`恢复的灾难性错误, 可以在极少数情况下调用。

### <a name="example"></a>示例

请参阅[CATCH](#catch)的示例。

### <a name="requirements"></a>要求

  **标头**afx

## <a name="see-also"></a>请参阅

[宏和全局](mfc-macros-and-globals.md)<br/>
[CException 类](cexception-class.md)<br/>
[CInvalidArgException 类](cinvalidargexception-class.md)
