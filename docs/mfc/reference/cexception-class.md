---
title: "CException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CException
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchException class, base class
- CException class
- exceptions, classes for
- CInternetException class, base class
- macros, exception handling
- CNotSupportedException class, base class
- CFileException class, base class
- CDBException class, base class
- CArchiveException class, base class
- CUserException class
- CDaoException class, base class
- CMemoryException class, base class
- COleException class, base class
- CResourceException class, base class
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 4cbb69ff79a1b201260d83b1bd568b63519a33b5
ms.lasthandoff: 02/24/2017

---
# <a name="cexception-class"></a>CException 类
Microsoft 基础类库中所有异常的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class AFX_NOVTABLE CException : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CException::CException](#cexception)|构造 `CException` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CException::Delete](#delete)|删除`CException`对象。|  
|[CException::ReportError](#reporterror)|向用户报告一个消息框中的错误消息。|  
  
## <a name="remarks"></a>备注  
 因为`CException`是您不能创建一个抽象基类`CException`对象直接; 必须创建的派生类的对象。 如果您需要创建您自己`CException`的样式类，请使用上面列出作为模型的派生类之一。 请确保您的派生的类还使用`IMPLEMENT_DYNAMIC`。  
  
 下面列出了派生的类及其说明︰  
  
|||  
|-|-|  
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|资源重要的 MFC 异常的基类|  
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|无效参数异常条件|  
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|内存不足异常|  
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|不支持的操作的请求|  
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|特定于存档的异常|  
|[CFileException](../../mfc/reference/cfileexception-class.md)|特定于文件的异常|  
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|找不到或不能创建 Windows 资源|  
|[COleException](../../mfc/reference/coleexception-class.md)|OLE 异常|  
|[CDBException](../../mfc/reference/cdbexception-class.md)|数据库异常 （也就是说，对于基于开放式数据库连接的 MFC 数据库类引起的异常条件）|  
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|OLE 调度 （自动化） 异常|  
|[CUserException](../../mfc/reference/cuserexception-class.md)|异常，指示找不到资源|  
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|数据访问对象的异常 （也就是说，对于 DAO 类时产生的异常条件）|  
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Internet 异常 （即，Internet 类所引起的异常条件）。|  
  
 这些异常是为了与使用[引发](exception-processing.md#throw)， [THROW_LAST](exception-processing.md#throw_last)，[尝试](exception-processing.md#try)，[捕获](exception-processing.md#catch)， [and_catch](exception-processing.md#and_catch)，和[end_catch](exception-processing.md#end_catch)宏。 有关异常的详细信息，请参阅[异常处理](exception-processing.md)，或请参阅文章[异常处理 (MFC)](../exception-handling-in-mfc.md)。  
  
 若要捕获特定异常，使用的相应派生的类。 捕捉所有类型的异常，使用`CException`，然后使用[CObject::IsKindOf](cobject-class.md#iskindof)以区分各个`CException`的派生类。 请注意，`CObject::IsKindOf`仅适用于的类声明使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)宏，以便充分利用动态类型检查。 任何`CException`-您创建的派生的类应使用`IMPLEMENT_DYNAMIC`宏，太。  
  
 您可以通过调用详细信息报告有关用户的例外情况[GetErrorMessage](cfileexception-class.md#geterrormessage)或[ReportError](#reporterror)，两个成员函数采用了任一`CException`的派生类。  
  
 如果异常由某个宏，捕获`CException`自动删除对象; 不能删除自己。 如果通过使用捕获异常**捕获**关键字，不会自动删除。 请参阅文章[异常处理 (MFC)](../exception-handling-in-mfc.md)有关何时删除异常对象的详细信息。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](cobject-class.md)  
  
 `CException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="a-namecexceptiona--cexceptioncexception"></a><a name="cexception"></a>CException::CException  
 此成员函数所构造`CException`对象。  
  
```  
explicit CException(BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>参数  
 *b_AutoDelete*  
 指定**TRUE**如果的内存`CException`在堆中分配对象。 这将导致`CException`时删除的对象**删除**调用成员函数删除异常。 指定**FALSE**如果`CException`对象在堆栈上是否是一个全局对象。 在这种情况下，`CException`对象将无法删除时**删除**调用成员函数。  
  
### <a name="remarks"></a>备注  
 永远不会正常情况下需要直接调用此构造函数。 将引发异常的函数应创建的实例`CException`的派生类并调用其构造函数，也应使用的 MFC 引发是否如函数、 [AfxThrowFileException](exception-processing.md#afxthrowfileexception)、 引发预定义的类型。 本文档提供仅出于完整性的考虑。  
  
##  <a name="a-namedeletea--cexceptiondelete"></a><a name="delete"></a>CException::Delete  
 此函数将检查以查看**CException**位于堆上，创建对象，如果是这样，它调用**删除**对象上的运算符。  
  
```  
void Delete();
```  
  
### <a name="remarks"></a>备注  
 在删除时**CException**对象，请使用**删除**成员函数删除异常。 请不要使用**删除**运算符直接，因为`CException`对象可能是一个全局对象，或在堆栈中创建。  
  
 您可以指定在构造的对象时是否应删除该对象。 有关详细信息，请参阅[CException::CException](#cexception)。  
  
 只需调用**删除**如果您使用的 c + +**尝试**- **捕获**机制。 如果您使用 MFC 宏**尝试**和**捕获**，则这些宏将自动调用此函数。  
  
### <a name="example"></a>示例  
 ```cpp  
 CFile* pFile = NULL;
// Constructing a CFile object with this override may throw
// a CFile exception, and won't throw any other exceptions.
// Calling CString::Format() may throw a CMemoryException,
// so we have a catch block for such exceptions, too. Any
// other exception types this function throws will be
// routed to the calling function.
// Note that this example performs the same actions as the 
// example for CATCH, but uses C++ try/catch syntax instead
// of using the MFC TRY/CATCH macros. This sample must use
// CException::Delete() to delete the exception objects
// before closing the catch block, while the CATCH example
// implicitly performs the deletion via the macros.
try
{
   pFile = new CFile(_T("C:\\WINDOWS\\SYSTEM.INI"),
      CFile::modeRead | CFile::shareDenyNone);
   ULONGLONG ullLength = pFile->GetLength();
   CString str;
   str.Format(_T("Your SYSTEM.INI file is %u bytes long."), ullLength);
   AfxMessageBox(str);
}
catch(CFileException* pEx)
{
   // Simply show an error message to the user.
   pEx->ReportError();
   pEx->Delete();
}
catch(CMemoryException* pEx)
{
   // We can't recover from this memory exception, so we'll
   // just terminate the app without any cleanup. Normally, an
   // an application should do everything it possibly can to
   // clean up properly and _not_ call AfxAbort().
   pEx->Delete();
   AfxAbort();
}
// If an exception occurrs in the CFile constructor,
// the language will free the memory allocated by new
// and will not complete the assignment to pFile.
// Thus, our clean-up code needs to test for NULL.
if (pFile != NULL)
{
   pFile->Close();
   delete pFile;
}   
 ```
  
##  <a name="a-namereporterrora--cexceptionreporterror"></a><a name="reporterror"></a>CException::ReportError  
 在向用户的消息框中调用此成员函数可对报表错误文本。  
  
```  
virtual int ReportError(
    UINT nType = MB_OK,  
    UINT nMessageID = 0);
```  
  
### <a name="parameters"></a>参数  
 `nType`  
 指定消息框的样式。 应用的任意组合[消息框样式](message-box-styles.md)的框。 如果未指定此参数，默认值是**MB_OK**。  
  
 *nMessageID*  
 指定要显示如果异常对象不具有一条错误消息的消息的资源 ID （字符串表条目）。 如果为 0，该消息"没有错误消息可用于"会显示。  
  
### <a name="return-value"></a>返回值  
 `AfxMessageBox`值; 否则为 0，如果内存不足，无法显示消息框。 请参阅[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)有关可能的返回值。  
  
### <a name="example"></a>示例  
 下面是一个示例使用`CException::ReportError`。 另一个示例，请参阅示例[捕获](exception-processing.md#catch)。  
  
```cpp  
CFile fileInput;
CFileException ex;

// try to open a file for reading.  
// The file will certainly not
// exist because there are too many explicit
// directories in the name.

// if the call to Open() fails, ex will be
// initialized with exception
// information.  the call to ex.ReportError() will
// display an appropriate
// error message to the user, such as
// "\Too\Many\Bad\Dirs.DAT contains an
// invalid path."  The error message text will be
// appropriate for the
// file name and error condition.

if (!fileInput.Open(_T("\\Too\\Many\\Bad\\Dirs.DAT"), CFile::modeRead, &ex))
{
  ex.ReportError();
}
else
{
  // the file was opened, so do whatever work
  // with fileInput we were planning...

  fileInput.Close();
}
```

## <a name="see-also"></a>另请参阅  
 [CObject 类](cobject-class.md)   
 [层次结构图](../hierarchy-chart.md)   
 [异常处理](exception-processing.md)   
 [如何︰ 创建我自己的自定义异常类](http://go.microsoft.com/fwlink/linkid=128045)



