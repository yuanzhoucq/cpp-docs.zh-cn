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
ms.openlocfilehash: 557bfe1cc41c3dda65bd95d7d687820c0b9862b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368333"
---
# <a name="cresourceexception-class"></a>CResourceException 类

当 Windows 无法找到或分配请求的资源时生成。

## <a name="syntax"></a>语法

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[资源异常：C 资源异常](#cresourceexception)|构造 `CResourceException` 对象。|

## <a name="remarks"></a>备注

没有必要或可能进一步的资格。

有关 使用`CResourceException`的详细信息，请参阅[异常处理 （MFC） 一](../../mfc/exception-handling-in-mfc.md)文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cresourceexceptioncresourceexception"></a><a name="cresourceexception"></a>资源异常：C 资源异常

构造 `CResourceException` 对象。

```
CResourceException();
```

### <a name="remarks"></a>备注

不要直接使用此构造函数，而应调用全局函数[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)。 有关异常的详细信息，请参阅[MFC 中的异常处理](../exception-handling-in-mfc.md)一文。

## <a name="see-also"></a>另请参阅

[CException 类](cexception-class.md)<br/>
[层次结构图表](../hierarchy-chart.md)
