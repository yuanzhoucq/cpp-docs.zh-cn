---
title: 异常处理 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.exceptions
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a24d78089e468a2020e0ecdb1fba34783965325
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376983"
---
# <a name="exception-processing"></a>异常处理
程序执行时，可以发生的异常条件和称为"异常"的错误数。 其中可能包括耗尽内存、 资源分配错误和文件中查找失败。  
  
 Microsoft 基础类库使用模仿密切一个由 ANSI 标准委员会建议用于 c + + 异常处理方案。 在调用函数可能会遇到反常情况之前，必须设置的异常处理程序。 如果该函数时遇到异常条件，则会引发异常并将控制传递到异常处理程序。  
  
 包含带有 Microsoft 基础类库的几个宏都将设置异常处理程序。 全局函数中的大量帮助引发专用的异常并终止程序，如有必要。 这些宏和全局函数分为以下类别：  
  
- 异常宏，结构异常处理程序。  
  
- Exception-throwing 函数)，其生成特定类型的异常。  
  
- 终止函数，这会使程序终止。  
  
 有关示例和更多详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="exception-macros"></a>异常宏  
  
|||  
|-|-|  
|[重](#try)|指定异常处理的代码的块。|  
|[捕获](#catch)|将捕获的异常从前面的代码块指定**重**块。|  
|[CATCH_ALL](#catch_all)|指定的用于捕获所有异常从前面的代码块**重**块。|  
|[AND_CATCH](#and_catch)|指定的用于捕获从前面的其他异常类型的代码块**重**块。|  
|[AND_CATCH_ALL](#and_catch_all)|指定的用于捕获中前面引发其他所有其他异常类型的代码块**重**块。|  
|[END_CATCH](#end_catch)|结束最后**捕获**或`AND_CATCH`代码块。|  
|[END_CATCH_ALL](#end_catch_all)|结束最后`CATCH_ALL`代码块。|  
|[引发](#throw)|将指定的异常引发。|  
|[THROW_LAST](#throw_last)|会引发到下一步的外部处理程序当前已处理的异常。|  
  
### <a name="exception-throwing-functions"></a>异常引发函数  
  
|||  
|-|-|  
|[AfxThrowArchiveException](#afxthrowarchiveexception)|引发存档异常。|  
|[AfxThrowFileException](#afxthrowfileexception)|将引发文件异常。|  
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|将引发无效参数异常。|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|将引发内存异常。|  
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|会引发不受支持的异常。|  
|[AfxThrowResourceException](#afxthrowresourceexception)|会引发 Windows 未找到资源的异常。|  
|[AfxThrowUserException](#afxthrowuserexception)|在用户启动程序操作中引发异常。|  
  
 专门为 OLE 异常，MFC 提供了两个异常引发函数：  
  
### <a name="ole-exception-functions"></a>OLE 异常函数  
  
|||  
|-|-|  
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|引发在 OLE 自动化函数中的异常。|  
|[AfxThrowOleException](#afxthrowoleexception)|引发 OLE 异常。|  
  
 若要支持数据库异常，数据库类提供两个异常类，`CDBException`和`CDaoException`，和全局函数，以支持异常类型：  
  
### <a name="dao-exception-functions"></a>DAO 异常函数  
  
|||  
|-|-|  
|[AfxThrowDAOException](#afxthrowdaoexception)|引发[CDaoException](../../mfc/reference/cdaoexception-class.md)从你自己的代码。|  
|[AfxThrowDBException](#afxthrowdbexception)|引发[CDBException](../../mfc/reference/cdbexception-class.md)从你自己的代码。|  
  
 MFC 提供了以下的终止函数：  
  
### <a name="termination-functions"></a>终止函数  
  
|||  
|-|-|  
|[AfxAbort](#afxabort)|调用终止应用程序时出现错误时发生。|  
  
##  <a name="try"></a>  重  
 将设置**重**块。  
  
```   
TRY   
```  
  
### <a name="remarks"></a>备注  
 A**重**块标识的可能会引发异常的代码块。 在下面的示例处理这些异常**捕获**和`AND_CATCH`块。 允许递归： 异常可能会传递给为外部**重**块，请忽略它们，或使用`THROW_LAST`宏。 结束**重**块`END_CATCH`或`END_CATCH_ALL`宏。  
  
 有关详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>示例  
 请参阅示例[捕获](#catch)。  

### <a name="requirements"></a>要求
标头：afx.h

##  <a name="catch"></a>  捕获  
 定义的捕获引发在前面的第一个异常类型的代码块**重**块。  
  
```   
CATCH(exception_class, exception_object_pointer_name)  
 
```  
  
### <a name="parameters"></a>参数  
 *exception_class*  
 指定要测试的异常类型。 标准异常类的列表，请参阅类[CException](../../mfc/reference/cexception-class.md)。  
  
 *exception_object_pointer_name*  
 为将由宏创建的异常对象指针指定名称。 你可以使用指针名访问中的异常对象**捕获**块。 已为您声明此变量。  
  
### <a name="remarks"></a>备注  
 适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用 `THROW_LAST` 宏以将处理移动到下一个外部帧。 结束**重**块`END_CATCH`宏。  
  
 如果*exception_class*是类`CException`，然后将捕获所有异常类型。 你可以使用[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)成员函数来确定抛出的特定异常。 更好的方法来捕获的异常的几种类型是使用顺序`AND_CATCH`语句，每个都有不同的异常类型。  
  
 异常对象指针是由宏创建的。 不需要自行声明。  
  
> [!NOTE]
>  **捕获**块被定义为用大括号分隔的 c + + 作用域。 如果您在此范围中声明变量，则只能在该范围中访问它们。 这也适用于*exception_object_pointer_name*。  
  
 有关异常的详细信息和**捕获**宏，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]  
  
##  <a name="catch_all"></a>  CATCH_ALL  
 定义的捕获引发在前面的所有异常类型的代码块**重**块。  
  
```   
CATCH_ALL(exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>参数  
 *exception_object_pointer_name*  
 为将由宏创建的异常对象指针指定名称。 您可以使用指针名访问 `CATCH_ALL` 块中的异常对象。 已为您声明此变量。  
  
### <a name="remarks"></a>备注  
 适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用 `THROW_LAST` 宏以将处理移动到下一个外部帧。 如果你使用`CATCH_ALL`，结束**重**块`END_CATCH_ALL`宏。  
  
> [!NOTE]
>  `CATCH_ALL` 块被定义为用大括号分隔的 C ++ 范围。 如果您在此范围中声明变量，则只能在该范围中访问它们。  
  
 有关异常的详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>示例  
 请参阅示例[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。  
  
### <a name="requirements"></a>要求  
  **标头**afx.h  

##  <a name="and_catch"></a>  AND_CATCH  
 定义的用于捕获中前面引发其他异常的代码块**重**块。  
  
```   
AND_CATCH(exception_class, exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>参数  
 *exception_class*  
 指定要测试的异常类型。 标准异常类的列表，请参阅类[CException](../../mfc/reference/cexception-class.md)。  
  
 *exception_object_pointer_name*  
 将由宏创建的异常对象指针名称。 您可以使用指针名访问 `AND_CATCH` 块中的异常对象。 已为您声明此变量。  
  
### <a name="remarks"></a>备注  
 使用**捕获**宏来捕获一个异常类型，则`AND_CATCH`宏来捕获每个后续的类型。 结束**重**块`END_CATCH`宏。  
  
 适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用`THROW_LAST`宏内的`AND_CATCH`阻止 shift 处理到下一步的外部异常帧。 `AND_CATCH` 标记的前面末尾**捕获**或`AND_CATCH`块。  
  
> [!NOTE]
>  `AND_CATCH`块被定义为 c + + 作用域 （用大括号分开）。 如果您声明此范围中的变量，请记住，它们只能在该作用域中访问。 这也适用于*exception_object_pointer_name*变量。  
  
### <a name="example"></a>示例  
 请参阅示例[捕获](#catch)。  
  
### <a name="requirements"></a>要求  
  **标头**afx.h  
##  <a name="and_catch_all"></a>  AND_CATCH_ALL  
 定义的用于捕获中前面引发其他异常的代码块**重**块。  
  
```   
AND_CATCH_ALL(exception_object_pointer_name)  
```  
  
### <a name="parameters"></a>参数  
 *exception_object_pointer_name*  
 将由宏创建的异常对象指针名称。 您可以使用指针名访问 `AND_CATCH_ALL` 块中的异常对象。 已为您声明此变量。  
  
### <a name="remarks"></a>备注  
 使用**捕获**宏来捕获一个异常类型，则`AND_CATCH_ALL`宏来捕获其他所有后续的类型。 如果你使用`AND_CATCH_ALL`，结束**重**块`END_CATCH_ALL`宏。  
  
 适当时，异常处理代码可以询问异常对象以获取有关异常的具体原因的详细信息。 调用`THROW_LAST`宏内的`AND_CATCH_ALL`阻止 shift 处理到下一步的外部异常帧。 `AND_CATCH_ALL` 标记的前面末尾**捕获**或`AND_CATCH_ALL`块。  
  
> [!NOTE]
>  `AND_CATCH_ALL`块被定义为 c + + 作用域 （用大括号分隔）。 如果您声明此范围中的变量，请记住，它们只能在该作用域中访问。  
  
### <a name="requirements"></a>要求  
  **标头**afx.h  
  
##  <a name="end_catch"></a>  END_CATCH  
 标记的最后一个结束**捕获**或`AND_CATCH`块。  
  
```   
END_CATCH  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息`END_CATCH`宏，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afx.h  
  
##  <a name="end_catch_all"></a>  END_CATCH_ALL  
 标记的最后一个结束`CATCH_ALL`或`AND_CATCH_ALL`块。  
  
```   
END_CATCH_ALL  
```  
  
### <a name="requirements"></a>要求  
  **标头**afx.h  
  
##  <a name="throw"></a>  THROW (MFC)  
 将指定的异常引发。  
  
```   
THROW(exception_object_pointer) 
```  
  
### <a name="parameters"></a>参数  
 *exception_object_pointer*  
 指向异常对象派生自`CException`。  
  
### <a name="remarks"></a>备注  
 **引发**中断程序的执行，将控件传递到关联**捕获**阻止在程序中。 如果你未提供**捕获**阻止，则控制权传递给一个打印错误消息并退出的 Microsoft 基础类库模块。  
  
 有关详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afx.h  
  
##  <a name="throw_last"></a>  THROW_LAST  
 异常引发回下一个外部**捕获**块。  
  
```   
THROW_LAST()   
```  
  
### <a name="remarks"></a>备注  
 此宏可以引发本地创建的异常。 如果你尝试引发异常，你只需捕获，它通常将超出范围，而且被删除。 与`THROW_LAST`，此异常正确传递到下一步**捕获**处理程序。  
  
 有关详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>示例  
 请参阅示例[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。  
  
### <a name="requirements"></a>要求  
  **标头**afx.h  
  
##  <a name="afxthrowarchiveexception"></a>  AfxThrowArchiveException  
 引发存档异常。  
  
```   
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName); 
```  
  
### <a name="parameters"></a>参数  
 `cause`  
 指定一个整数，指示该异常的原因。 有关可能的值的列表，请参阅[CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)。  
  
 `lpszArchiveName`  
 指向包含的名称的字符串`CArchive`导致异常，（如果可用） 的对象。  
  
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
 `cause`  
 指定一个整数，指示该异常的原因。 有关可能的值的列表，请参阅[CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause)。  
  
 `lOsError`  
 包含操作系统错误号 （如果可用），它指示异常的原因。 请参阅你操作系统手册了解错误代码的列表。  
  
 `lpszFileName`  
 指向包含导致异常，（如果可用） 文件的名称的字符串。  
  
### <a name="remarks"></a>备注  
 你负责确定基于操作系统错误代码的原因。  
  
### <a name="requirements"></a>要求  
  **标头**afx.h  

## <a name="afxthrowinvalidargexception"></a>  AfxThrowInvalidArgException
将引发无效参数异常。  
   
### <a name="syntax"></a>语法    
```
void AfxThrowInvalidArgException( );  
```  
   
### <a name="remarks"></a>备注  
 使用无效参数时，调用此函数。  
   
### <a name="requirements"></a>要求  
 **标头：** afx.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [CInvalidArgException 类](cinvalidargexception-class.md)   
 [引发](#throw)
  
  
##  <a name="afxthrowmemoryexception"></a>  AfxThrowMemoryException  
 将引发内存异常。  
  
```   
void AfxThrowMemoryException(); 
```  
  
### <a name="remarks"></a>备注  
 如果调用此函数对基础系统内存分配器的调用 (如`malloc`和[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) Windows 函数) 失败。 不需要调用它的**新**因为**新**自动将引发内存异常，如果内存分配失败。  
  
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
 将资源异常引发。  
  
```   
void  AfxThrowResourceException(); 
```  
  
### <a name="remarks"></a>备注  
 无法加载 Windows 资源时，通常会调用此函数。  
  
### <a name="requirements"></a>要求  
  **标头**afx.h  
  
##  <a name="afxthrowuserexception"></a>  AfxThrowUserException  
 引发异常来停止最终用户操作。  
  
```   
void AfxThrowUserException(); 
```  
  
### <a name="remarks"></a>备注  
 通常后立即调用此函数`AfxMessageBox`已向用户报告错误。  
  
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
 `wCode`  
 特定于应用程序的错误代码。  
  
 `lpszDescription`  
 错误的文字说明。  
  
 `nDescriptionID`  
 错误文字说明的资源 ID。  
  
 `nHelpID`  
 应用程序的帮助 (.HLP) 文件的帮助上下文。  
  
### <a name="remarks"></a>备注  
 提供给此函数的信息可由驱动应用程序（Microsoft Visual Basic 或其他 OLE 自动化客户端应用程序）显示。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afx.h  
  
##  <a name="afxthrowoleexception"></a>  AfxThrowOleException  
 创建类型的对象`COleException`并引发异常。  
  
``` 
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr); 
```  
  
### <a name="parameters"></a>参数  
 `sc`  
 指示该异常的原因的 OLE 状态代码。  
  
 `hr`  
 指示该异常的原因的结果代码的句柄。  
  
### <a name="remarks"></a>备注  
 采用的版本`HRESULT`如自变量将该结果代码转换为相应`SCODE`。 有关详细信息`HRESULT`和`SCODE`，请参阅[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)Windows SDK 中。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="afxthrowdaoexception"></a>  AfxThrowDaoException  
 调用此函数引发异常的类型[CDaoException](../../mfc/reference/cdaoexception-class.md)从你自己的代码。  
  
```   
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,  
    SCODE scode = S_OK); 
```  
  
### <a name="parameters"></a>参数  
 `nAfxDaoError`  
 表示扩展错误代码 DAO 的整数值，这可以值之一列入[CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)。  
  
 *scode*  
 OLE 错误代码，从 DAO，类型的`SCODE`。 有关信息，请参阅[CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)。  
  
### <a name="remarks"></a>备注  
 框架还调用`AfxThrowDaoException`。 在你调用中，可以传递的参数之一或两者。 例如，如果您想要提升之一错误中定义**CDaoException::nAfxDaoError**但你不关心*scode*参数，将传递中的有效代码`nAfxDaoError`参数并接受默认值为*scode*。  
  
 有关与 MFC DAO 类相关的异常的信息，请参阅类`CDaoException`在本书和文章[异常： 数据库异常](../../mfc/exceptions-database-exceptions.md)。  
  
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
 `nRetCode`  
 类型的值**某一 RETCODE**，定义类型的错误导致引发异常。  
  
 `pdb`  
 指向的指针`CDatabase`表示异常与之关联的数据源连接的对象。  
  
 `hstmt`  
 一个 ODBC **HSTMT**指定异常与之关联的语句句柄的句柄。  
  
### <a name="remarks"></a>备注  
 框架调用`AfxThrowDBException`当它收到一个 ODBC**某一 RETCODE**从调用 ODBC API 函数，并解释**某一 RETCODE**为一个异常情况，而不是 expectable 错误。 例如，数据访问操作可能会由于磁盘读取错误而失败。  
  
 璝惠**某一 RETCODE**值由 ODBC，请参阅 Windows SDK 中的第 8 章"检索状态和错误信息"。 有关 MFC 扩展到这些代码的信息，请参阅类[CDBException](../../mfc/reference/cdbexception-class.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afx.h  
  
##  <a name="afxabort"></a>  AfxAbort  
 由 MFC 提供的默认终止函数。  
  
```   
void  AfxAbort(); 
```  
  
### <a name="remarks"></a>备注  
 `AfxAbort` 在内部调用由 MFC 成员函数是错误，例如不能处理未捕获的异常时。 你可以调用`AfxAbort`遇到出现灾难性错误无法恢复时的罕见情况。  
  
### <a name="example"></a>示例  
 请参阅示例[捕获](#catch)。  

### <a name="requirements"></a>要求  
  **标头**afx.h   
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)   
 [CException 类](../../mfc/reference/cexception-class.md)
