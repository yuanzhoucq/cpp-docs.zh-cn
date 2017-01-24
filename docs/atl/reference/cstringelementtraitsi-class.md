---
title: "CStringElementTraitsI Class | Microsoft Docs"
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
  - "ATL::CStringElementTraitsI"
  - "CStringElementTraitsI"
  - "ATL.CStringElementTraitsI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringElementTraitsI class"
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStringElementTraitsI Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供静态函数与集合选件类对象存储的字符串相关。  它类似于 [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)，但是，执行不区分大小写的比较。  
  
## 语法  
  
```  
  
      template<  
   typename T,  
   class CharTraits = CDefaultCharTraits< T::XCHAR >  
>  
class CStringElementTraitsI : public CElementTraitsBase< T >  
```  
  
#### 参数  
 `T`  
 要存储在集合中的数据的类型。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CStringElementTraitsI::INARGTYPE](../Topic/CStringElementTraitsI::INARGTYPE.md)|使用的数据类型对于将元素添加到集合选件类对象。|  
|[CStringElementTraitsI::OUTARGTYPE](../Topic/CStringElementTraitsI::OUTARGTYPE.md)|使用的数据类型对于检索元素集合选件类对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CStringElementTraitsI::CompareElements](../Topic/CStringElementTraitsI::CompareElements.md)|调用此静态函数来比较两个字符串是否相等元素，则忽略差异，以防。|  
|[CStringElementTraitsI::CompareElementsOrdered](../Topic/CStringElementTraitsI::CompareElementsOrdered.md)|调用此静态函数来比较两个字符串元素，则忽略差异，以防。|  
|[CStringElementTraitsI::Hash](../Topic/CStringElementTraitsI::Hash.md)|调用此静态函数计算给定字符串元素的哈希值。|  
  
## 备注  
 此选件类提供静态函数用于比较字符串以及创建哈希值。  使用时，集合选件类存储字符串根据数据，这些功能很有用。  当字符串对象是已处理的引用时，请使用 [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)。  
  
 有关更多信息，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 继承层次结构  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringElementTraitsI`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CElementTraitsBase Class](../../atl/reference/celementtraitsbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CStringElementTraits Class](../../atl/reference/cstringelementtraits-class.md)