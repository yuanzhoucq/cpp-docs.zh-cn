---
title: "Implementing CComObject, CComAggObject, and CComPolyObject | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CComPolyObject"
  - "CComAggObject"
  - "CComObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAggObject class"
  - "CComObject class, 实现"
  - "CComPolyObject class, 实现"
  - "CreateInstance 方法"
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing CComObject, CComAggObject, and CComPolyObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类 [CComObject](../atl/reference/ccomobject-class.md)，[CComAggObject](../atl/reference/ccomaggobject-class.md)，并且，[CComPolyObject](../atl/reference/ccompolyobject-class.md) 始终是继承链的派生类。  是它们的职责到方法的句柄都在 **IUnknown**的: `QueryInterface`、 `AddRef`和 **Release**。  此外，`CComAggObject` 和 `CComPolyObject` \(当用于合成对象\)提供特定引用对于内部未知和 `QueryInterface` 语义所需的计数。  
  
 是否使用 `CComObject`、 `CComAggObject`或 `CComPolyObject` 取决于是否声明之一\(或\)下面的宏:  
  
|宏|效果|  
|-------|--------|  
|`DECLARE_NOT_AGGREGATABLE`|始终使用 `CComObject`。|  
|`DECLARE_AGGREGATABLE`|使用 `CComAggObject`，如果对象是聚合和 `CComObject`，如果未启用。  `CComCoClass` 因此包含此宏，如果 **DECLARE\_\*\_AGGREGATABLE** 宏都在您的选件类没有声明为，这将是默认设置。|  
|`DECLARE_ONLY_AGGREGATABLE`|始终使用 `CComAggObject`。  如果对象不进行聚合，返回false。|  
|`DECLARE_POLY_AGGREGATABLE`|当 **IClassFactory::CreateInstance** 调用时，ATL创建 **CComPolyObject\<CYourClass\>** 实例。  在创建时，外部未知的值进行检查。  如果是 **NULL**，**IUnknown** 为一nonaggregated对象实现。  如果外部未知不是 **NULL**，**IUnknown** 为一个复合的对象实现。|  
  
 使用 `CComAggObject` 和 `CComObject` 的优点是 **IUnknown** 的实现所创建的命名对象转换。  例如，在中，而合成对象需要内部未知的引用计数以及指向外部未知，一nonaggregated对象只需要引用计数。  
  
 使用 `CComPolyObject` 的优点是您避免为 `CComAggObject` 和 `CComObject` 在的模块处理合成和nonaggregated大小写。  一个 `CComPolyObject` 对象处理两种情况。  这意味着只有一个副本的vtable和函数的一个副本存在于您的模块。  如果vtable大，则可以显着降低您的模块范围。  但是，因此，如果vtable很小，使用 `CComPolyObject` 从而导致一个稍微大的模块范围，因为它没有为一个复合的或nonaggregated对象转换，如 `CComAggObject` 和 `CComObject`。  
  
## 请参阅  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)   
 [Aggregation and Class Factory Macros](../atl/reference/aggregation-and-class-factory-macros.md)