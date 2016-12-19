---
title: "CComPtr Class | Microsoft Docs"
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
  - "CComPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComPtr class"
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

托管COM接口指针的智能指针选件类。  
  
## 语法  
  
```  
  
      template<  
   class T   
>  
class CComPtr  
```  
  
#### 参数  
 `T`  
 指定指针类型的COM接口将存储。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CComPtr::CComPtr](../Topic/CComPtr::CComPtr.md)|构造函数。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[CComPtr::operator \=](../Topic/CComPtr::operator%20=.md)|分配指向成员的指针。|  
  
## 备注  
 ATL使用 `CComPtr` 和 [CComQIPtr](../../atl/reference/ccomqiptr-class.md) 管理COM接口指针。  两个从 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)派生，因此，两个执行自动引用计数。  
  
 **CComPtr** 和 [CComQIPtr](../../atl/reference/ccomqiptr-class.md) 选件类可帮助通过消除了内存泄漏自动引用计数。  以下功能两个执行逻辑相同操作;但是，请注意第二个版本如何可能不太容易出错的使用 **CComPtr** 选件类:  
  
 [!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/CPP/ccomptr-class_1.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/CPP/ccomptr-class_2.cpp)]  
  
 在调试版本中，代码跟踪链接atlsd.lib。  
  
## 继承层次结构  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 `CComPtr`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [CComPtr::CComPtr](../Topic/CComPtr::CComPtr.md)   
 [CComQIPtr::CComQIPtr](../Topic/CComQIPtr::CComQIPtr.md)   
 [Class Overview](../../atl/atl-class-overview.md)