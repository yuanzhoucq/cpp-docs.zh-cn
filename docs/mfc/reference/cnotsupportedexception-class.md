---
title: CNotSupportedException 类
ms.date: 11/04/2016
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
ms.openlocfilehash: b859b939baef018e69b245e597eea90e608253ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363198"
---
# <a name="cnotsupportedexception-class"></a>CNotSupportedException 类

表示因请求不支持的功能而引起的异常。

## <a name="syntax"></a>语法

```
class CNotSupportedException : public CSimpleException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[不支持的例外：：不支持例外](#cnotsupportedexception)|构造 `CNotSupportedException` 对象。|

## <a name="remarks"></a>备注

没有必要或可能进一步的资格。

有关 使用`CNotSupportedException`的详细信息，请参阅[异常处理 （MFC） 一](../../mfc/exception-handling-in-mfc.md)文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cnotsupportedexceptioncnotsupportedexception"></a><a name="cnotsupportedexception"></a>不支持的例外：：不支持例外

构造 `CNotSupportedException` 对象。

```
CNotSupportedException();
```

### <a name="remarks"></a>备注

不要直接使用此构造函数，而是调用全局函数[AfxThrowNot 支持异常](exception-processing.md#afxthrownotsupportedexception)。 有关异常处理的详细信息，请参阅[MFC 中的异常处理](../exception-handling-in-mfc.md)一文。

## <a name="see-also"></a>另请参阅

[CException 类](cexception-class.md)<br/>
[层次结构图表](../hierarchy-chart.md)
