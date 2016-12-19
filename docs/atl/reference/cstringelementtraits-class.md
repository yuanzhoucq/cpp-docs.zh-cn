---
title: "CStringElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CStringElementTraits<T>"
  - "ATL::CStringElementTraits<T>"
  - "CStringElementTraits"
  - "ATL.CStringElementTraits"
  - "ATL::CStringElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringElementTraits class"
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStringElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供集合选件使用类的静态函数存储 `CString` 对象。  
  
## 语法  
  
```  
  
      template<  
   typename T   
>  
class CStringElementTraits  
```  
  
#### 参数  
 `T`  
 要存储在集合中的数据的类型。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CStringElementTraits::INARGTYPE](../Topic/CStringElementTraits::INARGTYPE.md)|使用的数据类型对于将元素添加到集合选件类对象。|  
|[CStringElementTraits::OUTARGTYPE](../Topic/CStringElementTraits::OUTARGTYPE.md)|使用的数据类型对于检索元素集合选件类对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CStringElementTraits::CompareElements](../Topic/CStringElementTraits::CompareElements.md)|（静态）调用此函数来比较两个字符串是否相等元素。|  
|[CStringElementTraits::CompareElementsOrdered](../Topic/CStringElementTraits::CompareElementsOrdered.md)|（静态）调用此函数来比较两个字符串元素。|  
|[CStringElementTraits::CopyElements](../Topic/CStringElementTraits::CopyElements.md)|（静态）调用此功能复制到集合选件类对象中存储的 `CString` 元素。|  
|[CStringElementTraits::Hash](../Topic/CStringElementTraits::Hash.md)|（静态）调用此函数计算给定字符串元素的哈希值。|  
|[CStringElementTraits::RelocateElements](../Topic/CStringElementTraits::RelocateElements.md)|（静态）调用此函数重新定位在集合选件类对象中存储的 `CString` 元素。|  
  
## 备注  
 此选件类提供静态函数提供复制，移动和比较字符串以及创建哈希值。  使用时，集合选件类存储字符串根据数据，这些功能很有用。  在需要时，请使用 [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) 不区分大小写的比较。  当字符串对象将托管引用时，请使用 [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)。  
  
 有关更多信息，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 要求  
 **Header:** cstringt.h  
  
## 请参阅  
 [CElementTraitsBase Class](../../atl/reference/celementtraitsbase-class.md)   
 [CStringElementTraitsI Class](../../atl/reference/cstringelementtraitsi-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)