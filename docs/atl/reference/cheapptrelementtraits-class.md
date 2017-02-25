---
title: "CHeapPtrElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CHeapPtrElementTraits"
  - "CHeapPtrElementTraits"
  - "ATL::CHeapPtrElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtrElementTraits class"
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CHeapPtrElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在创建堆指针时的集合，此选件类的方法、静态有用功能和的typedef。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
typename T,  
class Allocator= ATL::CCRTAllocator  
>  
class CHeapPtrElementTraits : public CDefaultElementTraits<  
ATL::CHeapPtr< T, Allocator>  
>  
```  
  
#### 参数  
 `T`  
 在集合选件类中存储的对象类型。  
  
 `Allocator`  
 对于使用的内存分配选件类。  默认值为 [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CHeapPtrElementTraits::INARGTYPE](../Topic/CHeapPtrElementTraits::INARGTYPE.md)|使用的数据类型对于将元素添加到集合选件类对象。|  
|[CHeapPtrElementTraits::OUTARGTYPE](../Topic/CHeapPtrElementTraits::OUTARGTYPE.md)|使用的数据类型对于检索元素集合选件类对象。|  
  
## 备注  
 此选件类用于帮助集合包含堆指针的选件类对象的创建的方法、静态函数和typedef。  选件类 `CHeapPtrList` 从 `CHeapPtrElementTraits`派生。  
  
 有关更多信息，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 继承层次结构  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CHeapPtrElementTraits`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CDefaultElementTraits Class](../../atl/reference/cdefaultelementtraits-class.md)   
 [CComHeapPtr Class](../../atl/reference/ccomheapptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)