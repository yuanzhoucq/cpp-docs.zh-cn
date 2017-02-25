---
title: "CAutoVectorPtr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAutoVectorPtr"
  - "ATL.CAutoVectorPtr"
  - "ATL.CAutoVectorPtr<T>"
  - "CAutoVectorPtr"
  - "ATL::CAutoVectorPtr<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoVectorPtr class"
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CAutoVectorPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用新的向量和删除运算符，此选件类表示智能指针对象。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
typename T  
> class CAutoVectorPtr  
```  
  
#### 参数  
 `T`  
 指针类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAutoVectorPtr::CAutoVectorPtr](../Topic/CAutoVectorPtr::CAutoVectorPtr.md)|构造函数。|  
|[CAutoVectorPtr::~CAutoVectorPtr](../Topic/CAutoVectorPtr::~CAutoVectorPtr.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAutoVectorPtr::Allocate](../Topic/CAutoVectorPtr::Allocate.md)|调用此方法分配 `CAutoVectorPtr`所指向的一些需要对象的内存。|  
|[CAutoVectorPtr::Attach](../Topic/CAutoVectorPtr::Attach.md)|调用此方法将现有指针的所有权。|  
|[CAutoVectorPtr::Detach](../Topic/CAutoVectorPtr::Detach.md)|调用此方法释放指针的所有权。|  
|[CAutoVectorPtr::Free](../Topic/CAutoVectorPtr::Free.md)|调用此方法删除点的对象。`CAutoVectorPtr`。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAutoVectorPtr::operator T \*](../Topic/CAutoVectorPtr::operator%20T%20*.md)|转换运算符。|  
|[CAutoVectorPtr::operator \=](../Topic/CAutoVectorPtr::operator%20=.md)|赋值运算符。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAutoVectorPtr::m\_p](../Topic/CAutoVectorPtr::m_p.md)|指针数据成员变量。|  
  
## 备注  
 此选件类为创建和管理智能指针提供方法，这将有助于防止内存泄漏通过自动释放资源，则应该超出范围时。  `CAutoVectorPtr` 类似于 `CAutoPtr`，唯一的区别该 `CAutoVectorPtr` 使用 [新的向量&#91;&#93;](../Topic/operator%20new\(%3Cnew%3E\).md) 和 [向量删除&#91;&#93;](../Topic/operator%20delete\(%3Cnew%3E\).md) 分配和释放内存而不是C\+\+ **new** 和 **delete** 运算符。  如果需要，请参见 [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)`CAutoVectorPtr` 集合选件类。  
  
 有关使用示例智能指针选件类参见 [CAutoPtr](../../atl/reference/cautoptr-class.md)。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [CAutoPtr Class](../../atl/reference/cautoptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)