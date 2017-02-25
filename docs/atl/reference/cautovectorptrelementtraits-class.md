---
title: "CAutoVectorPtrElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAutoVectorPtrElementTraits<T>"
  - "ATL.CAutoVectorPtrElementTraits"
  - "ATL.CAutoVectorPtrElementTraits<T>"
  - "ATL::CAutoVectorPtrElementTraits"
  - "CAutoVectorPtrElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoVectorPtrElementTraits class"
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CAutoVectorPtrElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在创建智能指针使用新的向量和删除运算符时的集合，此选件类的方法、静态有用功能和的typedef。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
typename T  
>  
class CAutoVectorPtrElementTraits : public CDefaultElementTraits<  
ATL::CAutoVectorPtr< T>  
>  
```  
  
#### 参数  
 `T`  
 指针类型。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|描述|  
|--------|--------|  
|[CAutoVectorPtrElementTraits::INARGTYPE](../Topic/CAutoVectorPtrElementTraits::INARGTYPE.md)|使用的数据类型对于将元素添加到集合选件类对象。|  
|[CAutoVectorPtrElementTraits::OUTARGTYPE](../Topic/CAutoVectorPtrElementTraits::OUTARGTYPE.md)|使用的数据类型对于检索元素集合选件类对象。|  
  
## 备注  
 此选件类用于帮助集合包含智能指针的选件类对象的创建的方法、静态函数和typedef。  不同 [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)，此选件类使用新的向量和删除运算符。  
  
## 继承层次结构  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoVectorPtrElementTraits`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CDefaultElementTraits Class](../../atl/reference/cdefaultelementtraits-class.md)   
 [CAutoVectorPtr Class](../../atl/reference/cautovectorptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)