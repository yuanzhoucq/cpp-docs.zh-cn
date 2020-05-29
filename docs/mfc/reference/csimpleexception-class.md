---
title: CSimpleException 类
ms.date: 11/04/2016
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
ms.openlocfilehash: eb94ba9e3d26b3cd910f23c3d4abb29d3b8b1cd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318366"
---
# <a name="csimpleexception-class"></a>CSimpleException 类

此类是资源重要的 MFC 异常的基类。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[简单例外：：简单例外](#csimpleexception)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[简单例外：获取错误消息](#geterrormessage)|提供有关已发生错误的文本。|

## <a name="remarks"></a>备注

`CSimpleException`是资源关键型 MFC 异常的基本类，并处理错误消息的所有权和初始化。 以下类用作`CSimpleException`其基类：

|||
|-|-|
|[C内存异常类](../../mfc/reference/cmemoryexception-class.md)|内存不足异常|
|[CNotSupportedException 类](../../mfc/reference/cnotsupportedexception-class.md)|请求不支持的操作|
|[CResourceException 类](../../mfc/reference/cresourceexception-class.md)|找不到或无法创建的窗口资源|
|[用户例外类](../../mfc/reference/cuserexception-class.md)|指示找不到资源的异常|
|[CInvalidArgException 类](../../mfc/reference/cinvalidargexception-class.md)|指示无效参数的异常|

因为`CSimpleException`是抽象基类，因此不能直接声明`CSimpleException`对象。 相反，必须声明派生对象，如上表中的对象。 如果要声明自己的派生类，请使用前面的类作为模型。

有关详细信息，请参阅["例外类"](../../mfc/reference/cexception-class.md)主题和[异常处理 （MFC）。](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a>简单例外：：简单例外

构造函数。

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>参数

*b自动删除*<br/>
如果`CSimpleException`对象的内存已在堆上分配，请指定 TRUE。 这将导致在`CSimpleException`调用`Delete`成员函数删除异常时删除对象。 如果对象位于堆`CSimpleException`栈上或是全局对象，请指定 FALSE。 在这种情况下，`CSimpleException`在调用`Delete`成员函数时不会删除该对象。

### <a name="remarks"></a>备注

您通常不需要直接调用此构造函数。 引发异常的函数应创建`CException`派生类的实例并调用其构造函数，或者它应该使用 MFC 引发函数之一（如[AfxThrowFileexception）](exception-processing.md#afxthrowfileexception)来引发预定义类型。

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a>简单例外：获取错误消息

调用此成员函数以提供有关已发生的错误的文本。

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>参数

*lpsz错误*<br/>
指向将接收错误消息的缓冲区的指针。

*nMax错误*<br/>
缓冲区可以保留的最大字符数，包括 NULL 终止符。

*pnHelpContext*<br/>
将收到帮助上下文 ID 的 UINT 的地址。 如果 NULL，则不会返回任何 ID。

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0 如果没有错误消息文本可用。

### <a name="remarks"></a>备注

有关详细信息，请参阅["例外：获取错误消息](../../mfc/reference/cfileexception-class.md#geterrormessage)"。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CException 类](../../mfc/reference/cexception-class.md)<br/>
[异常处理](../../mfc/exception-handling-in-mfc.md)
