---
title: "CHeapPtrList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CHeapPtrList"
  - "CHeapPtrList"
  - "ATL.CHeapPtrList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtrList class"
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CHeapPtrList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当构造列表堆指针时，此选件类提供有用的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
typename E,  
class Allocator = ATL::CCRTAllocator  
>  
class CHeapPtrList : public CAtlList<  
ATL::CHeapPtr< E, Allocator>,  
CHeapPtrElementTraits< E, Allocator>  
>  
```  
  
#### 参数  
 `E`  
 在集合选件类中存储的对象类型。  
  
 `Allocator`  
 对于使用的内存分配选件类。  默认值为 [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CHeapPtrList::CHeapPtrList](../Topic/CHeapPtrList::CHeapPtrList.md)|构造函数。|  
  
## 备注  
 此选件类提供一个构造函数并从 [CAtlList](../../atl/reference/catllist-class.md) 和 [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) 派生方法帮助存储区堆指针的集合选件类对象的创建。  
  
## 继承层次结构  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CHeapPtrList`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CAtlList Class](../../atl/reference/catllist-class.md)   
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrElementTraits Class](../../atl/reference/cheapptrelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)