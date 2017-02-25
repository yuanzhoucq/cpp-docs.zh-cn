---
title: "IAtlStringMgr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IAtlStringMgr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAtlStringMgr class"
  - "内存, 管理"
  - "shared classes, IAtlStringMgr"
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# IAtlStringMgr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示接口。`CStringT` 内存管理器。  
  
## 语法  
  
```  
  
__interface IAtlStringMgr  
  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[分配](../Topic/IAtlStringMgr::Allocate.md)|调用此方法将一个新字符串数据结构。|  
|[Clone](../Topic/IAtlStringMgr::Clone.md)|调用此方法返回指向一个新字符串管理器用于 `CSimpleStringT`另一个实例的使用。|  
|[自由](../Topic/IAtlStringMgr::Free.md)|调用此方法可释放字符串数据结构。|  
|[GetNilString](../Topic/IAtlStringMgr::GetNilString.md)|返回指向空字符串对象使用的 `CStringData` 对象。|  
|[重新分配](../Topic/IAtlStringMgr::Reallocate.md)|调用此方法分配字符串数据结构。|  
  
## 备注  
 此接口管理MFC无关的字符选件类使用的内存;例如 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)、 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)和 [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)。  
  
 还可以使用此选件类实现自己的自定义字符串选件类的自定义内存管理器。  有关更多信息，请参见 [内存管理和CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## 要求  
 **Header:** atlsimpstr.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)