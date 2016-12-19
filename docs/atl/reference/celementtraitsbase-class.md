---
title: "CElementTraitsBase Class | Microsoft Docs"
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
  - "CElementTraitsBase"
  - "ATL::CElementTraitsBase"
  - "ATL.CElementTraitsBase<T>"
  - "ATL::CElementTraitsBase<T>"
  - "ATL.CElementTraitsBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CElementTraitsBase class"
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CElementTraitsBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供默认副本，并且集合的移动方案类别。  
  
## 语法  
  
```  
  
      template<  
   typename T  
>  
class CElementTraitsBase  
```  
  
#### 参数  
 `T`  
 要存储在集合中的数据的类型。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CElementTraitsBase::INARGTYPE](../Topic/CElementTraitsBase::INARGTYPE.md)|使用的数据类型对于将元素添加到集合选件类对象。|  
|[CElementTraitsBase::OUTARGTYPE](../Topic/CElementTraitsBase::OUTARGTYPE.md)|使用的数据类型对于检索元素集合选件类对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CElementTraitsBase::CopyElements](../Topic/CElementTraitsBase::CopyElements.md)|调用此方法复制到集合选件类对象存储的元素。|  
|[CElementTraitsBase::RelocateElements](../Topic/CElementTraitsBase::RelocateElements.md)|调用此方法定位在集合选件类对象存储的元素。|  
  
## 备注  
 该基类定义复制的方法，并在集合中定位的元素类别。  选件类使用它 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)、 [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)和 [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。  
  
 有关更多信息，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)