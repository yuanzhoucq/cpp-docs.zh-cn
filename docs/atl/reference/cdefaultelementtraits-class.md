---
title: "CDefaultElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CDefaultElementTraits<T>"
  - "ATL.CDefaultElementTraits"
  - "ATL::CDefaultElementTraits"
  - "ATL.CDefaultElementTraits<T>"
  - "CDefaultElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDefaultElementTraits class"
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CDefaultElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供默认方法，并收集的功能类别。  
  
## 语法  
  
```  
  
      template<  
   typename T  
>  
class CDefaultElementTraits : public CElementTraitsBase< T >,  
   public CDefaultHashTraits< T >,  
   public CDefaultCompareTraits< T >  
```  
  
#### 参数  
 `T`  
 要存储在集合中的数据的类型。  
  
## 备注  
 此选件类提供默认静态函数，并移动，复制，比较和集合中存储的哈希的组件的方法类别对象。  从 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)、 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)和 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)派生其功能和方法 [CElementTraits](../../atl/reference/celementtraits-class.md)、 [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)和 [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)使用此选件类。  
  
 有关更多信息，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)