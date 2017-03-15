---
title: "IUnknown Implementation Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.Iunknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUnknown implementation classes"
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# IUnknown Implementation Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面选件类执行 **IUnknown** 和相关方法:  
  
-   [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) 管理引用计数合成和nonaggregated对象的。  允许您指定线程模型。  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) 管理引用计数合成和nonaggregated对象的。  使用服务器上的默认线程模型。  
  
-   一个复合对象的[CComAggObject](../atl/reference/ccomaggobject-class.md) 实现 **IUnknown**。  
  
-   一nonaggregated对象的[CComObject](../atl/reference/ccomobject-class.md) 实现 **IUnknown**。  
  
-   [CComPolyObject](../atl/reference/ccompolyobject-class.md) 实现合成和nonaggregated对象的 **IUnknown**。  使用 `CComPolyObject` 避免为 `CComAggObject` 和 `CComObject` 在的模块。  一个 `CComPolyObject` 对象处理聚合并nonaggregated大小写。  
  
-   [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) 实现一nonaggregated对象的 **IUnknown**，而不修改模块锁计数。  
  
-   拖曳接口的[CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) 实现 **IUnknown**。  
  
-   “缓存的”的[CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) 实现 **IUnknown** 拖曳接口。  
  
-   [CComContainedObject](../atl/reference/ccomcontainedobject-class.md) 实现摘要或拖曳接口的内部对象的 **IUnknown**。  
  
-   [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) 尝试在模块的引用数确保您的对象不会被删除。  
  
-   使用 **IUnknown**的一个骨骼实现，[CComObjectStack](../atl/reference/ccomobjectstack-class.md) 创建一个临时的COM对象。  
  
## 相关文章  
 [ATL COM对象的基本知识](../atl/fundamentals-of-atl-com-objects.md)  
  
## 请参阅  
 [Class Overview](../atl/atl-class-overview.md)   
 [Aggregation and Class Factory Macros](../atl/reference/aggregation-and-class-factory-macros.md)   
 [COM Map Macros](../atl/reference/com-map-macros.md)   
 [COM Map Global Functions](../atl/reference/com-map-global-functions.md)