---
title: CComObjectRoot 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
dev_langs:
- C++
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93d30c1af67159c04546076a07c78fbaec9cbb91
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762314"
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

[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
[CComAggObject 类](../../atl/reference/ccomaggobject-class.md)   
[CComObject 类](../../atl/reference/ccomobject-class.md)   
[CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)   
[类概述](../../atl/atl-class-overview.md)
