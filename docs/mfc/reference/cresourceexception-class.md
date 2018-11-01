---
title: CResourceException 类
ms.date: 11/04/2016
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
ms.openlocfilehash: aa7fd6e2caa15a256cec2eae5ede6c6e47cd1518
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632672"
---
# <a name="cresourceexception-class"></a>CResourceException 类

当 Windows 无法找到或分配请求的资源时生成。

## <a name="syntax"></a>语法

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|构造 `CResourceException` 对象。|

## <a name="remarks"></a>备注

没有进一步限定是需要或不能。

有关使用的详细信息`CResourceException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cresourceexception"></a>  CResourceException::CResourceException

构造 `CResourceException` 对象。

```
CResourceException();
```

### <a name="remarks"></a>备注

请勿直接，使用此构造函数而不是调用全局函数[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)。 有关异常的详细信息，请参阅文章[MFC 中的异常处理](../exception-handling-in-mfc.md)。

## <a name="see-also"></a>请参阅

[CException 类](cexception-class.md)<br/>
[层次结构图](../hierarchy-chart.md)

