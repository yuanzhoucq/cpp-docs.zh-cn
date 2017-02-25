---
title: "CPrimitiveElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CPrimitiveElementTraits<T>"
  - "CPrimitiveElementTraits"
  - "ATL.CPrimitiveElementTraits"
  - "ATL::CPrimitiveElementTraits<T>"
  - "ATL::CPrimitiveElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrimitiveElementTraits class"
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CPrimitiveElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为集合选件类提供默认方法和函数中对基元数据类型。  
  
## 语法  
  
```  
  
      template<  
   typename T  
> class CPrimitiveElementTraits :   
   public CDefaultElementTraits< T >  
```  
  
#### 参数  
 `T`  
 在集合选件类对象中存储的数据类型。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|描述|  
|--------|--------|  
|[CPrimitiveElementTraits::INARGTYPE](../Topic/CPrimitiveElementTraits::INARGTYPE.md)|使用的数据类型对于将元素添加到集合选件类对象。|  
|[CPrimitiveElementTraits::OUTARGTYPE](../Topic/CPrimitiveElementTraits::OUTARGTYPE.md)|使用的数据类型对于检索元素集合选件类对象。|  
  
## 备注  
 此选件类提供默认静态函数，并移动，复制，比较和散列的基元数据类型的集合中存储的元素的方法类别对象。  
  
 有关更多信息，请参见 [ATL集合选件类](../../atl/atl-collection-classes.md)。  
  
## 继承层次结构  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CPrimitiveElementTraits`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CDefaultElementTraits Class](../../atl/reference/cdefaultelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)