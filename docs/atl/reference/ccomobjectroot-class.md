---
title: CComObjectRoot 类
ms.date: 11/04/2016
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
ms.openlocfilehash: 4761aa9ae9c8ffacfb393311d7e058b1450b4628
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554960"
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot 类

Typedef [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)针对线程处理模型的服务器的默认模板化。

## <a name="syntax"></a>语法

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>备注

`CComObjectRoot` 是`typedef`的[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)针对线程处理模型的服务器的默认模板化。 从而[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)将引用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。

`CComObjectRootEx` 处理非聚合和聚合对象的对象引用计数管理。 如果您的对象未被聚合，并且如果您的对象正在聚合包含指向未知的外部，它保留对象引用计数。 对于聚合对象，`CComObjectRootEx`方法可用于处理的内部对象失败，若要构造，并保护中删除发布内部接口时的外部对象或内部对象删除。

## <a name="requirements"></a>要求

**标头：** atlcom.h

## <a name="see-also"></a>请参阅

[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComAggObject 类](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 类](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
