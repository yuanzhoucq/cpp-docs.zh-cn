---
title: "CDefaultHashTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDefaultHashTraits"
  - "ATL.CDefaultHashTraits<T>"
  - "ATL::CDefaultHashTraits<T>"
  - "ATL.CDefaultHashTraits"
  - "ATL::CDefaultHashTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDefaultHashTraits class"
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CDefaultHashTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类用于计算哈希值提供静态函数。  
  
## 语法  
  
```  
  
      template<  
   typename T  
>  
class CDefaultHashTraits  
```  
  
#### 参数  
 `T`  
 要存储在集合中的数据的类型。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDefaultHashTraits::Hash](../Topic/CDefaultHashTraits::Hash.md)|（静态）调用此函数计算给定元素的哈希值。|  
  
## 备注  
 此选件类包含返回特定元素的哈希值的单个静态函数。  [CDefaultElementTraits选件类](../../atl/reference/cdefaultelementtraits-class.md)使用此选件类。  
  
 有关更多信息，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)