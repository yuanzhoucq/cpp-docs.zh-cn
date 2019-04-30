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
ms.openlocfilehash: c3af508cd39e277ca4ae0a9aad5e639f66edc53b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407921"
---
# <a name="cnotsupportedexception-class"></a>CNotSupportedException 类

表示因请求不支持的功能而引起的异常。

## <a name="syntax"></a>语法

```
class CNotSupportedException : public CSimpleException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|构造 `CNotSupportedException` 对象。|

## <a name="remarks"></a>备注

没有进一步限定是需要或不能。

有关使用的详细信息`CNotSupportedException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="cnotsupportedexception"></a>  CNotSupportedException::CNotSupportedException

构造 `CNotSupportedException` 对象。

```
CNotSupportedException();
```

### <a name="remarks"></a>备注

请勿直接，使用此构造函数而不是调用全局函数[AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception)。 有关异常处理的详细信息，请参阅文章[MFC 中的异常处理](../exception-handling-in-mfc.md)。

## <a name="see-also"></a>请参阅

[CException 类](cexception-class.md)<br/>
[层次结构图](../hierarchy-chart.md)
