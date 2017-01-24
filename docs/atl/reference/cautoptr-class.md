---
title: "CAutoPtr Class | Microsoft Docs"
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
  - "CAutoPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoPtr class"
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAutoPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示智能指针对象。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<   
typename T  
>  
class CAutoPtr  
```  
  
#### 参数  
 `T`  
 指针类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CAutoPtr::CAutoPtr](../Topic/CAutoPtr::CAutoPtr.md)|构造函数。|  
|[CAutoPtr::~CAutoPtr](../Topic/CAutoPtr::~CAutoPtr.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CAutoPtr::Attach](../Topic/CAutoPtr::Attach.md)|调用此方法将现有指针的所有权。|  
|[CAutoPtr::Detach](../Topic/CAutoPtr::Detach.md)|调用此方法释放指针的所有权。|  
|[CAutoPtr::Free](../Topic/CAutoPtr::Free.md)|调用此方法删除点的对象。`CAutoPtr`。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[CAutoPtr::operator T\*](../Topic/CAutoPtr::operator%20T*.md)|转换运算符。|  
|[CAutoPtr::operator \=](../Topic/CAutoPtr::operator%20=.md)|赋值运算符。|  
|[CAutoPtr::operator \-\>](../Topic/CAutoPtr::operator%20-%3E.md)|指向成员的指针运算符。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[CAutoPtr::m\_p](../Topic/CAutoPtr::m_p.md)|指针数据成员变量。|  
  
## 备注  
 此选件类为创建和管理智能指针提供方法，这将有助于防止内存泄漏通过自动释放资源，则应该超出范围时。  
  
 此外，`CAutoPtr`的复制构造函数和赋值运算符调用，复制源指针到目标指针和设置源指针的指针的所有权更改为NULL。  有两 `CAutoPtr` 对象存储同一指针的每个因此是不可能的，这样，减少两次删除同一指针的可能性。  
  
 `CAutoPtr` 还简化指针的集合的创建。  而不是派生集合选件类并重写析构函数，较为简单的进行集合 `CAutoPtr` 对象。  在集合中删除，`CAutoPtr` 对象将超出范围并自动删除它。  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md) 和变量与 `CAutoPtr`类似方式工作，不同之处在于，它们分配和释放内存使用不同的堆函数而不是C\+\+ **新建** 和 **delete** 运算符。  [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) 类似于 `CAutoPtr`，唯一的区别它使用 **vector new\[\]** 和 **vector delete\[\]** 分配和释放内存。  
  
 请参见 [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) 和 [CAutoPtrList](../../atl/reference/cautoptrlist-class.md)，当数组或列表智能指针需要。  
  
## 要求  
 **Header:** atlbase.h  
  
## 示例  
 [!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/CPP/cautoptr-class_1.cpp)]  
  
## 请参阅  
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CAutoVectorPtr Class](../../atl/reference/cautovectorptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)