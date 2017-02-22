---
title: "CStringRefElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStringRefElementTraits"
  - "ATL.CStringRefElementTraits"
  - "ATL::CStringRefElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringRefElementTraits class"
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CStringRefElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供静态函数与集合选件类对象存储的字符串相关。  字符串对象处理引用。  
  
## 语法  
  
```  
  
      template<   
   typename T  
>  
class CStringRefElementTraits : public CElementTraitsBase< T >  
```  
  
#### 参数  
 `T`  
 要存储在集合中的数据的类型。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CStringRefElementTraits::CompareElements](../Topic/CStringRefElementTraits::CompareElements.md)|调用此静态函数来比较两个字符串是否相等元素。|  
|[CStringRefElementTraits::CompareElementsOrdered](../Topic/CStringRefElementTraits::CompareElementsOrdered.md)|调用此静态函数来比较两个字符串元素。|  
|[CStringRefElementTraits::Hash](../Topic/CStringRefElementTraits::Hash.md)|调用此静态函数计算给定字符串元素的哈希值。|  
  
## 备注  
 此选件类提供静态函数用于比较字符串以及创建哈希值。  使用时，集合选件类存储字符串根据数据，这些功能很有用。  不同 [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) 和 [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)，`CStringRefElementTraits` 导致 `CString` 参数将作为 **const CString&** 引用。  
  
 有关更多信息，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 继承层次结构  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringRefElementTraits`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CElementTraitsBase Class](../../atl/reference/celementtraitsbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)