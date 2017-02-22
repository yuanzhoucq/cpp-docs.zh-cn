---
title: "CAutoPtrElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAutoPtrElementTraits"
  - "CAutoPtrElementTraits"
  - "ATL::CAutoPtrElementTraits<T>"
  - "ATL.CAutoPtrElementTraits<T>"
  - "ATL::CAutoPtrElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoPtrElementTraits class"
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CAutoPtrElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在创建智能指针时的集合，此选件类的方法、静态有用功能和的typedef。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
typename T  
>  
class CAutoPtrElementTraits : public CDefaultElementTraits<  
ATL::CAutoPtr< T>  
>  
```  
  
#### 参数  
 `T`  
 指针类型。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CAutoPtrElementTraits::INARGTYPE](../Topic/CAutoPtrElementTraits::INARGTYPE.md)|使用的数据类型对于将元素添加到集合选件类对象。|  
|[CAutoPtrElementTraits::OUTARGTYPE](../Topic/CAutoPtrElementTraits::OUTARGTYPE.md)|使用的数据类型对于检索元素集合选件类对象。|  
  
## 备注  
 此选件类用于帮助集合包含智能指针的选件类对象的创建的方法、静态函数和typedef。  选件类 [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) 和 [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) 从 `CAutoPtrElementTraits`派生。  如果生成需要新的向量和删除运算符智能指针的集合，请使用 [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)。  
  
## 继承层次结构  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoPtrElementTraits`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CDefaultElementTraits Class](../../atl/reference/cdefaultelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)