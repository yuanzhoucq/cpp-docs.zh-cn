---
title: "ATL Collection and Enumerator Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "集合类, ATL"
  - "枚举数, ATL 类"
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Collection and Enumerator Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL提供以下选件类帮助您实现集合和枚举数。  
  
|类|说明|  
|-------|--------|  
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|集合接口实现|  
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|枚举器接口实现\(假定在一个STL兼容容器存储的数据\)|  
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|枚举器接口实现\(假定在数组中存储的数据\)|  
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|enumerator对象实现\(使用 `IEnumOnSTLImpl`\)|  
|[CComEnum](../atl/reference/ccomenum-class.md)|enumerator对象实现\(使用 `CComEnumImpl`\)|  
|[\_Copy](../atl/atl-copy-policy-classes.md)|复制策略类选件|  
|[\_CopyInterface](../atl/atl-copy-policy-classes.md)|复制策略类选件|  
|[CAdapt](../atl/reference/cadapt-class.md)|适配器选件类\(隐藏 **operator &** 允许 `CComPtr`、在STL容器要存储的 `CComQIPtr`和 `CComBSTR` \)|  
  
## 请参阅  
 [集合和枚举数](../atl/atl-collections-and-enumerators.md)