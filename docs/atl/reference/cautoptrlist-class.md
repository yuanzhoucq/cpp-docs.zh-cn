---
title: "CAutoPtrList Class | Microsoft Docs"
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
  - "ATL::CAutoPtrList"
  - "CAutoPtrList"
  - "ATL.CAutoPtrList"
  - "ATL::CAutoPtrList<E>"
  - "ATL.CAutoPtrList<E>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoPtrList class"
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAutoPtrList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当构造列出了智能指针时，此选件类提供有用的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
typename E  
>  
class CAutoPtrList : public CAtlList<  
ATL::CAutoPtr< E>,  
CAutoPtrElementTraits< E>  
>  
```  
  
#### 参数  
 `E`  
 指针类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CAutoPtrList::CAutoPtrList](../Topic/CAutoPtrList::CAutoPtrList.md)|构造函数。|  
  
## 备注  
 此选件类提供一个构造函数并从 [CAtlList](../../atl/reference/catllist-class.md) 和 [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) 派生方法帮助存储区智能指针的列表对象的创建。  选件类 [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) 为数组对象类似的功能。  
  
 有关更多信息，请参见 [ATL集合选件类](../../atl/atl-collection-classes.md)。  
  
## 继承层次结构  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CAutoPtrList`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CAtlList Class](../../atl/reference/catllist-class.md)   
 [CAutoPtrElementTraits Class](../../atl/reference/cautoptrelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)