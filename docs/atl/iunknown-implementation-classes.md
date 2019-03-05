---
title: IUnknown 实现类 (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.Iunknown
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
ms.openlocfilehash: 97ca30c90cb8fa85685e30aa61d954008cf7cc54
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297562"
---
# <a name="iunknown-implementation-classes"></a>IUnknown 实现类

以下类实现`IUnknown`和相关方法：

- [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)管理引用计数聚合和非聚合对象。 可以指定线程模型。

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md)管理引用计数聚合和非聚合对象。 使用线程处理模型的服务器的默认值。

- [CComAggObject](../atl/reference/ccomaggobject-class.md)实现`IUnknown`聚合对象。

- [CComObject](../atl/reference/ccomobject-class.md)实现`IUnknown`非聚合对象。

- [CComPolyObject](../atl/reference/ccompolyobject-class.md)实现`IUnknown`聚合和非聚合对象。 使用`CComPolyObject`避免了必须同时`CComAggObject`和`CComObject`在模块中。 单个`CComPolyObject`对象处理聚合和非聚合的情况。

- [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md)实现`IUnknown`非聚合的对象，而无需修改的模块的锁计数。

- [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md)实现`IUnknown`分离式接口。

- [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md)实现`IUnknown`"缓存"分离式接口。

- [CComContainedObject](../atl/reference/ccomcontainedobject-class.md)实现`IUnknown`聚合或分离式接口的内部对象。

- [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md)管理模块以确保您的对象的引用计数不会删除。

- [CComObjectStack](../atl/reference/ccomobjectstack-class.md)创建一个临时的 COM 对象，使用的主干实现`IUnknown`。

## <a name="related-articles"></a>相关文章

[ATL COM 对象基础知识](../atl/fundamentals-of-atl-com-objects.md)

## <a name="see-also"></a>请参阅

[类概述](../atl/atl-class-overview.md)<br/>
[聚合和类工厂宏](../atl/reference/aggregation-and-class-factory-macros.md)<br/>
[COM 映射宏](../atl/reference/com-map-macros.md)<br/>
[COM 映射全局函数](../atl/reference/com-map-global-functions.md)
