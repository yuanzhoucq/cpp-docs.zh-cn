---
title: "CAutoPtrArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAutoPtrArray<E>"
  - "CAutoPtrArray"
  - "ATL::CAutoPtrArray"
  - "ATL.CAutoPtrArray<E>"
  - "ATL.CAutoPtrArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoPtrArray class"
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAutoPtrArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当构造一个数组智能指针时，此选件类提供有用的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
typename E  
>  
class CAutoPtrArray : public CAtlArray<  
ATL::CAutoPtr< E>,  
CAutoPtrElementTraits< E>  
>  
```  
  
#### 参数  
 `E`  
 指针类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAutoPtrArray::CAutoPtrArray](../Topic/CAutoPtrArray::CAutoPtrArray.md)|构造函数。|  
  
## 备注  
 此选件类提供一个构造函数并从 [CAtlArray](../../atl/reference/catlarray-class.md) 和 [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) 派生方法帮助存储区智能指针的集合选件类对象的创建。  
  
 有关更多信息，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 继承层次结构  
 `CAtlArray`  
  
 `CAutoPtrArray`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CAtlArray Class](../../atl/reference/catlarray-class.md)   
 [CAutoPtrElementTraits Class](../../atl/reference/cautoptrelementtraits-class.md)   
 [CAutoPtrList Class](../../atl/reference/cautoptrlist-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)