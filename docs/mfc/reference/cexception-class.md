---
title: CException 类
ms.date: 11/04/2016
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
ms.openlocfilehash: a24f324576c872e7fe509b742aa58d6c230ec24a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212483"
---
# <a name="cexception-class"></a>CException 类

Microsoft 基础类库中所有异常的基类。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CException：： CException](#cexception)|构造 `CException` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CException：:D e)](#delete)|删除 `CException` 对象。|
|[CException：： ReportError](#reporterror)|在消息框中向用户报告一条错误消息。|

## <a name="remarks"></a>备注

由于 `CException` 是抽象基类，因此您不能 `CException` 直接创建对象; 您必须创建派生类的对象。 如果需要创建您自己 `CException` 的类，请使用上面列出的派生类之一作为模型。 请确保派生类也使用 `IMPLEMENT_DYNAMIC` 。

下面列出了派生类及其说明：

|||
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|用于资源关键性的 MFC 异常的基类|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|参数异常条件无效|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|内存不足异常|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|请求不受支持的操作|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|存档特定的异常|
|[CFileException](../../mfc/reference/cfileexception-class.md)|文件特定的异常|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Windows 资源找不到或不可创建|
|[COleException](../../mfc/reference/coleexception-class.md)|OLE 异常|
|[CDBException](../../mfc/reference/cdbexception-class.md)|数据库异常（即，基于开放式数据库连接性而产生的针对 MFC 数据库类的异常情况）|
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|OLE 调度（automation）异常|
|[CUserException](../../mfc/reference/cuserexception-class.md)|指示找不到资源的异常|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|数据访问对象异常（即 DAO 类产生的异常条件）|
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Internet 例外（即 Internet 类产生的异常情况）。|

这些异常旨在与[THROW](exception-processing.md#throw)、 [THROW_LAST](exception-processing.md#throw_last)、 [try](exception-processing.md#try)、 [catch](exception-processing.md#catch)、 [and_catch](exception-processing.md#and_catch)和[end_catch](exception-processing.md#end_catch)宏一起使用。 有关异常的详细信息，请参阅[异常处理](exception-processing.md)，或参阅文章[异常处理（MFC）](../exception-handling-in-mfc.md)。

若要捕获特定的异常，请使用相应的派生类。 若要捕获所有类型的异常，请使用 `CException` ，然后使用[CObject：： IsKindOf](cobject-class.md#iskindof)来区分 `CException` 派生的类。 请注意， `CObject::IsKindOf` 仅适用于使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)宏声明的类，以便充分利用动态类型检查。 `CException`你创建的任何派生类也应该使用 `IMPLEMENT_DYNAMIC` 宏。

可以通过调用[GetErrorMessage](cfileexception-class.md#geterrormessage)或[ReportError](#reporterror)（两个适用于任何派生类的成员函数）向用户报告有关异常的详细信息 `CException` 。

如果某个宏捕获到异常，则 `CException` 会自动删除该对象; 不要自行删除。 如果使用关键字捕获到异常，则 **`catch`** 不会自动删除它。 有关何时删除异常对象的详细信息，请参阅文章[异常处理（MFC）](../exception-handling-in-mfc.md) 。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>要求

**标头：** afx

## <a name="cexceptioncexception"></a><a name="cexception"></a>CException：： CException

此成员函数构造 `CException` 对象。

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>参数

*b_AutoDelete*<br/>
如果 `CException` 已在堆上分配了对象的内存，则指定 TRUE。 这将导致在 `CException` `Delete` 调用成员函数删除异常时删除该对象。 如果 `CException` 对象位于堆栈上或是全局对象，则指定 FALSE。 在这种情况下， `CException` `Delete` 调用成员函数时不会删除对象。

### <a name="remarks"></a>备注

通常不需要直接调用此构造函数。 引发异常的函数应创建 `CException` 派生类的实例并调用其构造函数，或者应使用其中一种 MFC 引发函数（如[AfxThrowFileException](exception-processing.md#afxthrowfileexception)）来引发预定义类型。 提供此文档只是为了提供完整的完整性。

## <a name="cexceptiondelete"></a><a name="delete"></a>CException：:D e)

此函数检查是否 `CException` 在堆上创建了对象，如果是，则它对 **`delete`** 对象调用运算符。

```cpp
void Delete();
```

### <a name="remarks"></a>备注

删除对象时 `CException` ，请使用 `Delete` 成员函数删除该异常。 不要 **`delete`** 直接使用运算符，因为该 `CException` 对象可能是全局对象或已在堆栈上创建的。

可以指定在构造对象时是否应删除对象。 有关详细信息，请参阅[CException：： CException](#cexception)。

仅 `Delete` 当使用 c + + 机制时，才需要调用 **`try`** -  **`catch`** 。 如果使用的是 MFC 宏**TRY**和**CATCH**，则这些宏会自动调用此函数。

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

## <a name="cexceptionreporterror"></a><a name="reporterror"></a>CException：： ReportError

调用此成员函数可向用户报告消息框中的错误文本。

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>参数

nType**<br/>
指定消息框的样式。 将[消息框样式](styles-used-by-mfc.md#message-box-styles)的任意组合应用到框。 如果未指定此参数，则默认值为 MB_OK。

*nMessageID*<br/>
指定异常对象没有错误消息时要显示的消息的资源 ID （字符串表条目）。 如果为0，则显示消息 "没有可用的错误消息"。

### <a name="return-value"></a>返回值

一个 `AfxMessageBox` 值; 否则，如果没有足够的内存来显示消息框，则返回0。 有关可能的返回值，请参阅[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) 。

### <a name="example"></a>示例

下面是使用的示例 `CException::ReportError` 。 有关其他示例，请参阅[CATCH](exception-processing.md#catch)的示例。

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

[CObject 类](cobject-class.md)<br/>
[层次结构图](../hierarchy-chart.md)<br/>
[异常处理](exception-processing.md)<br/>
[如何实现：创建我自己的自定义异常类](https://go.microsoft.com/fwlink/p/?linkid=128045)
