---
title: "Properties and Property Pages Classes | Microsoft Docs"
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
  - "vc.atl.properties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "属性 [ATL]"
  - "属性 [ATL], 类"
  - "属性页, 类"
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Properties and Property Pages Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面选件类支持属性和属性页:  
  
-   [CComDispatchDriver](../Topic/CComDispatchDriver.md) 通过 `IDispatch` 指针检索或设置对象的属性。  
  
-   [CStockPropImpl](../atl/reference/cstockpropimpl-class.md) 实现ATL支持的常用属性。  
  
-   在对象的属性的调用的信息的[IPerPropertyBrowsingImpl](../atl/reference/iperpropertybrowsingimpl-class.md) 访问。  
  
-   [IPersistPropertyBagImpl](../atl/reference/ipersistpropertybagimpl-class.md) 在一个由客户端提供的属性包存储对象的属性。  
  
-   [IPropertyPageImpl](../atl/reference/ipropertypageimpl-class.md) 管理在属性表中的特定属性页。  
  
-   [IPropertyPage2Impl](../atl/reference/ipropertypage2impl-class.md) 类似于，`IPropertyPageImpl`，还允许客户端选择在属性页中的特定属性。  
  
-   [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md) 获取对象支持的属性页中的CLSID。  
  
## 相关文章  
 [ATL教程](../atl/active-template-library-atl-tutorial.md)  
  
 [ATL COM属性页](../atl/atl-com-property-pages.md)  
  
## 请参阅  
 [Class Overview](../atl/atl-class-overview.md)   
 [Property Map Macros](../atl/reference/property-map-macros.md)