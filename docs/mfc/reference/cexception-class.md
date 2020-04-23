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
ms.openlocfilehash: 93901f6f92ee79bd893b2ec0d1e341e77749d951
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753187"
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
|[例外：：例外](#cexception)|构造 `CException` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[例：:Delete](#delete)|删除`CException`对象。|
|[例外：报告错误](#reporterror)|向用户报告消息框中的错误消息。|

## <a name="remarks"></a>备注

因为`CException`是一个抽象的基类，`CException`你不能直接创建对象;必须创建派生类的对象。 如果需要创建自己的`CException`样式类，请使用上面列出的派生类之一作为模型。 确保派生类也使用`IMPLEMENT_DYNAMIC`。

派生类及其描述如下：

|||
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|资源关键型 MFC 异常的基类|
|[CInvalidArg例外](../../mfc/reference/cinvalidargexception-class.md)|无效参数异常条件|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|内存不足异常|
|[不支持例外](../../mfc/reference/cnotsupportedexception-class.md)|请求不支持的操作|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|特定于存档的异常|
|[CFileException](../../mfc/reference/cfileexception-class.md)|文件特定异常|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|找不到或无法创建的窗口资源|
|[COleException](../../mfc/reference/coleexception-class.md)|OLE 异常|
|[CDBException](../../mfc/reference/cdbexception-class.md)|数据库异常（即基于开放数据库连接的 MFC 数据库类产生的异常条件）|
|[COle调度例外](../../mfc/reference/coledispatchexception-class.md)|OLE 调度（自动化）异常|
|[CUserException](../../mfc/reference/cuserexception-class.md)|指示找不到资源的异常|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|数据访问对象异常（即 DAO 类产生的异常条件）|
|[C 互联网例外](../../mfc/reference/cinternetexception-class.md)|互联网例外（即，互联网类产生的异常条件）。|

这些异常旨在与[try](exception-processing.md#try)[THROW](exception-processing.md#throw)[THROW、THROW_LAST、](exception-processing.md#throw_last)尝试、[捕获](exception-processing.md#catch)[、and_catch](exception-processing.md#and_catch)和[end_catch](exception-processing.md#end_catch)宏一起使用。 有关异常的详细信息，请参阅[异常处理](exception-processing.md)，或请参阅文章[异常处理 （MFC）。](../exception-handling-in-mfc.md)

要捕获特定异常，请使用相应的派生类。 要捕获所有类型的异常，请使用 ，`CException`然后使用[CObject：：isKindOf](cobject-class.md#iskindof)来区分`CException`派生类。 请注意，`CObject::IsKindOf`仅适用于使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)宏声明的类，以便利用动态类型检查。 您`CException`创建的任何派生类也应使用`IMPLEMENT_DYNAMIC`宏。

您可以通过调用[GetErrorMessage](cfileexception-class.md#geterrormessage)或[ReportError](#reporterror)向用户报告有关异常的详细信息，这两个成员函数适用于任何`CException`派生类。

如果某个宏捕获了异常，则会自动删除该对象;`CException`如果某个宏捕获异常，则会自动删除该对象。不要自己删除它。 如果使用**catch**关键字捕获异常，则不会自动删除该异常。 有关何时删除解斥对象的详细信息，请参阅文章[异常处理 （MFC）。](../exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cexceptioncexception"></a><a name="cexception"></a>例外：：例外

此成员函数构造对象`CException`。

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>参数

*b_AutoDelete*<br/>
如果`CException`对象的内存已在堆上分配，请指定 TRUE。 这将导致在`CException`调用`Delete`成员函数删除异常时删除对象。 如果对象位于堆`CException`栈上或是全局对象，请指定 FALSE。 在这种情况下，`CException`在调用`Delete`成员函数时不会删除该对象。

### <a name="remarks"></a>备注

您通常不需要直接调用此构造函数。 引发异常的函数应创建`CException`派生类的实例并调用其构造函数，或者它应该使用 MFC 引发函数之一（如[AfxThrowFileexception）](exception-processing.md#afxthrowfileexception)来引发预定义类型。 本文档仅用于完整性。

## <a name="cexceptiondelete"></a><a name="delete"></a>例：:Delete

此函数检查`CException`对象是否在堆上创建，如果是，它将调用对象上的**delete**运算符。

```cpp
void Delete();
```

### <a name="remarks"></a>备注

删除对象时`CException`，`Delete`请使用成员函数删除异常。 不要直接使用**删除**运算符，因为`CException`对象可能是全局对象或在堆栈上创建的。

您可以指定在构造对象时是否应删除该对象。 有关详细信息，请参阅["例外：：例例](#cexception)"。

仅当使用C++`Delete`**尝试**- **捕获**机制时，才需要调用。 如果使用 MFC 宏**TRY**和**CATCH，** 则这些宏将自动调用此函数。

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

## <a name="cexceptionreporterror"></a><a name="reporterror"></a>例外：报告错误

调用此成员函数向用户报告消息框中的错误文本。

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>参数

nType**<br/>
指定消息框的样式。 将[消息框样式](styles-used-by-mfc.md#message-box-styles)的任意组合应用于该框。 如果不指定此参数，则默认值为MB_OK。

*nMessageID*<br/>
指定要显示的消息的资源 ID（字符串表条目），如果异常对象没有错误消息。 如果为 0，则显示"无错误消息可用"消息。

### <a name="return-value"></a>返回值

值`AfxMessageBox`;否则 0 如果没有足够的内存来显示消息框。 有关可能的返回值，请参阅[AfxMessageBox。](cstring-formatting-and-message-box-display.md#afxmessagebox)

### <a name="example"></a>示例

下面是 使用 的示例`CException::ReportError`。 对于另一个示例，请参阅[CATCH](exception-processing.md#catch)的示例。

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

## <a name="see-also"></a>请参阅

[CObject 类](cobject-class.md)<br/>
[层次结构图表](../hierarchy-chart.md)<br/>
[异常处理](exception-processing.md)<br/>
[如何操作：创建自己的自定义异常类](https://go.microsoft.com/fwlink/p/?linkid=128045)
