---
title: CSimpleException 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ab21338eabe2e432189ccf8a5aae3432005657d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083212"
---
# <a name="csimpleexception-class"></a>CSimpleException 类

此类是资源重要的 MFC 异常的基类。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSimpleException::CSimpleException](#csimpleexception)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSimpleException::GetErrorMessage](#geterrormessage)|提供有关已发生错误的文本。|

## <a name="remarks"></a>备注

`CSimpleException` 是资源重要的 MFC 异常的基类和处理的所有权和一条错误消息初始化。 下面的类使用`CSimpleException`作为其基类：

|||
|-|-|
|[CMemoryException 类](../../mfc/reference/cmemoryexception-class.md)|内存不足异常|
|[CNotSupportedException 类](../../mfc/reference/cnotsupportedexception-class.md)|不支持的操作的请求|
|[CResourceException 类](../../mfc/reference/cresourceexception-class.md)|找不到或不可创建的 Windows 资源|
|[CUserException 类](../../mfc/reference/cuserexception-class.md)|找不到表示资源的异常|
|[CInvalidArgException 类](../../mfc/reference/cinvalidargexception-class.md)|指示参数无效异常|

因为`CSimpleException`是一个抽象基类，您無法宣告`CSimpleException`直接对象。 相反，您必须声明派生的对象，如前面的表中。 如果要声明派生的类，用作模型的上一类。

有关详细信息，请参阅[CException 类](../../mfc/reference/cexception-class.md)主题和[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="csimpleexception"></a>  CSimpleException::CSimpleException

构造函数。

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>参数

*bAutoDelete*<br/>
如果指定为 TRUE 的内存`CSimpleException`已在堆上分配对象。 这将导致`CSimpleException`对象时删除`Delete`调用成员函数删除异常。 如果指定 FALSE`CSimpleException`对象位于堆栈，或者是一个全局对象。 在这种情况下，`CSimpleException`对象不会删除时`Delete`调用成员函数。

### <a name="remarks"></a>备注

通常情况下永远不需要直接调用此构造函数。 将引发异常的函数应创建的实例`CException`的派生的类并调用其构造函数，或它应使用的 MFC 会引发函数，如[AfxThrowFileException](exception-processing.md#afxthrowfileexception)、 引发预定义的类型。

##  <a name="geterrormessage"></a>  CSimpleException::GetErrorMessage

调用此成员函数以提供有关已发生错误的文本。

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>参数

*lpszError*<br/>
指向将收到一条错误消息的缓冲区的指针。

*nMaxError*<br/>
最大缓冲区可以保存，包括 NULL 终止符的字符数。

*pnHelpContext*<br/>
将收到帮助上下文 id。 UINT 的地址 如果为 NULL，则将返回没有 ID。

### <a name="return-value"></a>返回值

如果函数成功，则非零值否则，如果没有错误消息正文，则为 0 将用。

### <a name="remarks"></a>备注

有关详细信息，请参阅[CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CException 类](../../mfc/reference/cexception-class.md)<br/>
[异常处理](../../mfc/exception-handling-in-mfc.md)

