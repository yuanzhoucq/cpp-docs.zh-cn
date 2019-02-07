---
title: 异常处理
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.exceptions
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
ms.openlocfilehash: 8b40afbfcc453a4908b434dc53b7b86959673453
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55851677"
---
# <a name="exception-processing"></a>异常处理

程序执行时，会发生的异常情况和名为"异常"的错误数。 其中可能包括耗尽内存、 资源分配错误和查找文件失败。

Microsoft 基础类库使用只现代性密切 ANSI 标准委员会建议的 c + + 异常处理方案。 调用函数可能会遇到不正常情况之前，必须设置异常处理程序。 如果该函数时遇到异常条件，它引发异常，并控制传递到异常处理程序。

Microsoft 基础类库中包含的几个宏将设置异常处理程序。 多个其他全局函数帮助引发特殊的异常并终止程序，如有必要。 这些宏和全局函数划分为以下类别：

- 异常宏，结构异常处理程序。

- Exception-throwing 函数)，这会生成特定类型的异常。

- 终止函数，这会导致程序终止。

有关示例和更多详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="exception-macros"></a>异常宏

|||
|-|-|
|[TRY](#try)|将指定异常处理的代码的块。|
|[CATCH](#catch)|将指定的捕获的异常从前面的代码块**尝试**块。|
|[CATCH_ALL](#catch_all)|将指定的用于捕获所有异常从前面的代码块**尝试**块。|
|[AND_CATCH](#and_catch)|将指定的用于捕获从前面的其他异常类型的代码块**尝试**块。|
|[AND_CATCH_ALL](#and_catch_all)|将指定的用于捕获前面中引发的其他所有其他异常类型的代码块**尝试**块。|
|[END_CATCH](#end_catch)|结束最后**捕获**或**AND_CATCH**代码块。|
|[END_CATCH_ALL](#end_catch_all)|结束最后**CATCH_ALL**代码块。|
|[引发](#throw)|引发指定的异常。|
|[THROW_LAST](#throw_last)|将引发到下一个外部处理程序当前已处理的异常。|

### <a name="exception-throwing-functions"></a>异常引发函数

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|引发存档异常。|
|[AfxThrowFileException](#afxthrowfileexception)|将引发文件异常。|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|将引发无效参数异常。|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|将引发内存异常。|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|将引发不受支持的异常。|
|[AfxThrowResourceException](#afxthrowresourceexception)|会引发 Windows 资源未找到异常。|
|[AfxThrowUserException](#afxthrowuserexception)|在用户启动程序操作中引发异常。|

MFC 专门为 OLE 异常提供了两个异常引发函数：

### <a name="ole-exception-functions"></a>OLE 异常函数

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|则引发一个 OLE 自动化函数中的异常。|
|[AfxThrowOleException](#afxthrowoleexception)|引发 OLE 异常。|

若要支持数据库异常，数据库类提供两个异常类，`CDBException`和`CDaoException`，和全局函数来支持异常类型：

### <a name="dao-exception-functions"></a>DAO 异常函数

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|将引发[CDaoException](../../mfc/reference/cdaoexception-class.md)从你自己的代码。|
|[AfxThrowDBException](#afxthrowdbexception)|将引发[CDBException](../../mfc/reference/cdbexception-class.md)从你自己的代码。|

MFC 提供了以下的终止函数：

### <a name="termination-functions"></a>终止函数

|||
|-|-|
|[AfxAbort](#afxabort)|调用要终止的应用程序时出现错误时发生。|

##  <a name="try"></a>  TRY

设置了**尝试**块。

```
TRY
```

### <a name="remarks"></a>备注

一个**尝试**块标识可能会引发异常的代码块。 在下面的示例处理这些异常**捕获**并**AND_CATCH**块。 允许递归： 异常可能会传递到一个外部**尝试**块中的，通过忽略它们或通过使用 THROW_LAST 宏。 结束**尝试**END_CATCH 或 END_CATCH_ALL 宏块。

有关详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>示例

有关示例，请参阅[捕获](#catch)。

### <a name="requirements"></a>要求

标头：afx.h

##  <a name="catch"></a>  CATCH

定义的捕获引发在前面的第一个异常类型的代码块**尝试**块。

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_class*<br/>
指定要用于测试的异常类型。 标准异常类的列表，请参阅类[CException](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
为将由宏创建的异常对象指针指定名称。 可以使用指针名访问中的异常对象**捕获**块。 已为您声明此变量。

### <a name="remarks"></a>备注

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用 THROW_LAST 宏以将处理移动到下一个外部异常帧。 结束**尝试**END_CATCH 宏块。

如果*exception_class*是类`CException`，然后将捕获所有异常类型。 可以使用[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)成员函数以确定引发哪个异常。 更好的方法来捕获异常的几种类型是使用顺序**AND_CATCH**语句，每个都有不同的异常类型。

由宏创建异常对象指针。 不需要自行声明。

> [!NOTE]
>  **捕获**块被定义为用大括号分隔的 c + + 作用域。 如果您在此范围中声明变量，则只能在该范围中访问它们。 这同样适用于*exception_object_pointer_name*。

异常和 CATCH 宏的详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>  CATCH_ALL

定义的捕获所有异常类型引发在前面的代码块**尝试**块。

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_object_pointer_name*<br/>
为将由宏创建的异常对象指针指定名称。 您可以使用指针名访问 `CATCH_ALL` 块中的异常对象。 已为您声明此变量。

### <a name="remarks"></a>备注

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用 `THROW_LAST` 宏以将处理移动到下一个外部异常帧。 如果您使用**CATCH_ALL**，最终**尝试**END_CATCH_ALL 宏块。

> [!NOTE]
>  **CATCH_ALL**块被定义为用大括号分隔的 c + + 作用域。 如果您在此范围中声明变量，则只能在该范围中访问它们。

有关异常的详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>示例

有关示例，请参阅[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="and_catch"></a>  AND_CATCH

定义用于捕获前面中引发其他异常类型的代码块**尝试**块。

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_class*<br/>
指定要用于测试的异常类型。 标准异常类的列表，请参阅类[CException](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
将由宏创建异常对象指针的名称。 可以使用指针名访问中的异常对象**AND_CATCH**块。 已为您声明此变量。

### <a name="remarks"></a>备注

使用 CATCH 宏来捕获一个异常类型，则 AND_CATCH 宏来捕获每个后续类型。 结束**尝试**END_CATCH 宏块。

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用内的 THROW_LAST 宏**AND_CATCH**阻止把处理转移到下一个外部异常帧。 **AND_CATCH**标记前面的末尾**捕获**或**AND_CATCH**块。

> [!NOTE]
>  **AND_CATCH**块定义为 c + + 作用域 （用大括号分开）。 如果声明此范围中的变量，请记住它们是只能在该作用域中访问。 这同样适用于*exception_object_pointer_name*变量。

### <a name="example"></a>示例

有关示例，请参阅[捕获](#catch)。

### <a name="requirements"></a>要求

  **标头**afx.h
##  <a name="and_catch_all"></a>  AND_CATCH_ALL

定义用于捕获前面中引发其他异常类型的代码块**尝试**块。

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>参数

*exception_object_pointer_name*<br/>
将由宏创建异常对象指针的名称。 可以使用指针名访问中的异常对象**AND_CATCH_ALL**块。 已为您声明此变量。

### <a name="remarks"></a>备注

使用**捕获**宏来捕获一个异常类型，然后 AND_CATCH_ALL 宏以捕获其他所有后续类型。 如果使用 AND_CATCH_ALL，最终**尝试**END_CATCH_ALL 宏块。

适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用内的 THROW_LAST 宏**AND_CATCH_ALL**阻止把处理转移到下一个外部异常帧。 **AND_CATCH_ALL**标记前面的末尾**捕获**或**AND_CATCH_ALL**块。

> [!NOTE]
>  **AND_CATCH_ALL**块定义为 c + + 作用域 （用大括号分隔）。 如果声明此范围中的变量，请记住它们是只能在该作用域中访问。

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="end_catch"></a>  END_CATCH

标记的最后一个末尾**捕获**或**AND_CATCH**块。

```
END_CATCH
```

### <a name="remarks"></a>备注

有关 END_CATCH 宏的详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="end_catch_all"></a>  END_CATCH_ALL

标记的最后一个末尾<strong>CATCH_ALL88 或 * * AND_CATCH_ALL</strong>块。

```
END_CATCH_ALL
```

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="throw"></a>  THROW (MFC)

引发指定的异常。

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>参数

*exception_object_pointer*<br/>
指向异常对象派生自`CException`。

### <a name="remarks"></a>备注

**引发**中断程序执行，将控制传递到关联**捕获**中您的程序块。 如果你未提供**捕获**阻止，则控制权将传递给打印错误消息并退出的 Microsoft 基础类库模块。

有关详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="throw_last"></a>  THROW_LAST

异常引发回下一个外部**捕获**块。

```
THROW_LAST()
```

### <a name="remarks"></a>备注

此宏可引发本地创建的异常。 如果你尝试会引发异常，您只需捕获，它将通常会超出范围，并删除。 与**THROW_LAST**，此异常正确传递到下一步**捕获**处理程序。

有关详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>示例

有关示例，请参阅[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="afxthrowarchiveexception"></a>  AfxThrowArchiveException

引发存档异常。

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>参数

*cause*<br/>
指定一个整数，指示该异常的原因。 有关可能的值的列表，请参阅[CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)。

*lpszArchiveName*<br/>
指向包含名称的字符串`CArchive`（如果可用） 导致了异常的对象。

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="afxthrowfileexception"></a>  AfxThrowFileException

将引发文件异常。

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>参数

*cause*<br/>
指定一个整数，指示该异常的原因。 有关可能的值的列表，请参阅[CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause)。

*lOsError*<br/>
包含操作系统错误号 （如果可用），它指示该异常的原因。 请参阅你操作系统手册了解错误代码的列表。

*lpszFileName*<br/>
指向包含导致了异常 （如果可用） 的文件的名称的字符串。

### <a name="remarks"></a>备注

您负责确定基于操作系统错误代码的原因。

### <a name="requirements"></a>要求

  **标头**afx.h

## <a name="afxthrowinvalidargexception"></a>  AfxThrowInvalidArgException

将引发无效参数异常。

### <a name="syntax"></a>语法

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>备注

调用此函数时使用了无效的参数。

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxthrowmemoryexception"></a>  AfxThrowMemoryException

将引发内存异常。

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>备注

如果调用此函数对基础系统内存分配器的调用 (如**malloc**并[GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) Windows 函数) 失败。 不需要调用它的**新**因为**新**自动将引发内存异常，如果内存分配失败。

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="afxthrownotsupportedexception"></a>  AfxThrowNotSupportedException

将引发异常时不支持的功能请求的结果。

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="afxthrowresourceexception"></a>  AfxThrowResourceException

将引发资源异常。

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>备注

无法加载 Windows 资源时，通常情况下调用此函数。

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="afxthrowuserexception"></a>  AfxThrowUserException

引发异常来停止最终用户操作。

```
void AfxThrowUserException();
```

### <a name="remarks"></a>备注

此函数通常之后立即调用`AfxMessageBox`向用户报告了错误。

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="afxthrowoledispatchexception"></a>  AfxThrowOleDispatchException

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

  **标头**afx.h

##  <a name="afxthrowoleexception"></a>  AfxThrowOleException

创建类型的对象`COleException`则会引发异常。

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

Hresult 作为参数的版本将相应 SCODE 转换为该结果代码。 HRESULT 和 SCODE 的详细信息，请参阅[COM 错误代码的结构](/windows/desktop/com/structure-of-com-error-codes)Windows SDK 中。

### <a name="requirements"></a>要求

  **标头**afxdao.h

##  <a name="afxthrowdaoexception"></a>  AfxThrowDaoException

调用此函数可引发类型的异常[CDaoException](../../mfc/reference/cdaoexception-class.md)从你自己的代码。

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>参数

*nAfxDaoError*<br/>
一个整数值，表示 DAO 扩展错误代码，这可以值之一列入[CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)。

*scode*<br/>
从 DAO，类型 SCODE 的 OLE 错误代码。 有关信息，请参阅[CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)。

### <a name="remarks"></a>备注

框架还调用`AfxThrowDaoException`。 在您调用中，可以传递的参数之一或两者。 例如，如果你想要引发一个错误中定义**CDaoException::nAfxDaoError**但你不关心*scode*参数，传递有效的代码中*nAfxDaoError*参数并接受的默认值为*scode*。

与 MFC DAO 类相关的异常有关的信息，请参阅类`CDaoException`在此书和文章[异常：数据库异常](../../mfc/exceptions-database-exceptions.md)。

### <a name="requirements"></a>要求

  **标头**afxdb.h

##  <a name="afxthrowdbexception"></a>  AfxThrowDBException

调用此函数引发异常的类型`CDBException`从你自己的代码。

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>参数

*nRetCode*<br/>
类型 RETCODE，导致要引发的异常错误的类型定义的值。

*pdb*<br/>
一个指向`CDatabase`对象，表示该异常相关联的数据源连接。

*hstmt*<br/>
指定异常与之关联的语句句柄 ODBC HSTMT 句柄。

### <a name="remarks"></a>备注

框架将调用`AfxThrowDBException`ODBC RETCODE 收到对 ODBC API 函数的调用和将 RETCODE 解释为异常情况而不是 expectable 错误时。 例如，数据访问操作可能会因磁盘读取错误而失败。

由 ODBC 定义的某一 RETCODE 值有关的信息，请参阅 Windows SDK 中的第 8 章"检索状态和错误信息"。 有关 MFC 扩展到这些代码的信息，请参阅类[CDBException](../../mfc/reference/cdbexception-class.md)。

### <a name="requirements"></a>要求

  **标头**afx.h

##  <a name="afxabort"></a>  AfxAbort

由 MFC 提供的默认终止函数。

```
void  AfxAbort();
```

### <a name="remarks"></a>备注

`AfxAbort` 会在内部调用 MFC 成员函数时出现错误，例如，不能处理的未捕获异常。 您可以调用`AfxAbort`时遇到灾难性错误无法恢复的极少数情况。

### <a name="example"></a>示例

有关示例，请参阅[捕获](#catch)。

### <a name="requirements"></a>要求

  **标头**afx.h

## <a name="see-also"></a>请参阅

[宏和全局函数](mfc-macros-and-globals.md)<br/>
[CException 类](cexception-class.md)<br/>
[CInvalidArgException 类](cinvalidargexception-class.md)
