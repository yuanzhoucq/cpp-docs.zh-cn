---
title: IUnknown 实现类 (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.Iunknown
dev_langs:
- C++
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d67b2a7b9769acd7d6e596e4fcdf1aec30bbf74
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="iunknown-implementation-classes"></a>IUnknown 实现类
下面的类实现**IUnknown**及相关方法：  
  
-   [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)管理引用计数用于聚合和非聚合对象。 使用此选项可以指定线程处理模型。  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md)管理引用计数用于聚合和非聚合对象。 使用默认的线程处理模型的服务器。  
  
-   [CComAggObject](../atl/reference/ccomaggobject-class.md)实现**IUnknown**聚合对象。  
  
-   [CComObject](../atl/reference/ccomobject-class.md)实现**IUnknown**非聚合对象。  
  
-   [CComPolyObject](../atl/reference/ccompolyobject-class.md)实现**IUnknown**聚合和非聚合对象。 使用`CComPolyObject`避免必须同时`CComAggObject`和`CComObject`在模块中。 单个`CComPolyObject`对象处理聚合和非聚合的情况。  
  
-   [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md)实现**IUnknown**非聚合的对象，而无需修改的模块锁计数。  
  
-   [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md)实现**IUnknown**分离式接口。  
  
-   [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md)实现**IUnknown** "缓存"分离式接口。  
  
-   [CComContainedObject](../atl/reference/ccomcontainedobject-class.md)实现**IUnknown**聚合或分离式接口的内部对象。  
  
-   [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md)管理上的模块，以确保你的对象的引用计数不会删除。  
  
-   [CComObjectStack](../atl/reference/ccomobjectstack-class.md)创建一个临时的 COM 对象，使用的主干实现**IUnknown**。  
  
## <a name="related-articles"></a>相关文章  
 [ATL COM 对象基础知识](../atl/fundamentals-of-atl-com-objects.md)  
  
## <a name="see-also"></a>请参阅  
 [类概述](../atl/atl-class-overview.md)   
 [聚合和类工厂宏](../atl/reference/aggregation-and-class-factory-macros.md)   
 [COM 映射宏](../atl/reference/com-map-macros.md)   
 [COM 映射全局函数](../atl/reference/com-map-global-functions.md)

