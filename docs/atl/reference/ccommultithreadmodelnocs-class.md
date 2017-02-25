---
title: "CComMultiThreadModelNoCS Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComMultiThreadModelNoCS"
  - "CComMultiThreadModelNoCS"
  - "ATL.CComMultiThreadModelNoCS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 多线程处理"
  - "CComMultiThreadModelNoCS class"
  - "线程处理 [ATL]"
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CComMultiThreadModelNoCS Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComMultiThreadModelNoCS` 为递增和递减变量的值提供线程安全的方法，即，不使用锁或打开功能的临界区。  
  
## 语法  
  
```  
  
class CComMultiThreadModelNoCS  
  
```  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|描述|  
|--------|--------|  
|[CComMultiThreadModelNoCS::AutoCriticalSection](../Topic/CComMultiThreadModelNoCS::AutoCriticalSection.md)|引用选件类 [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|  
|[CComMultiThreadModelNoCS::CriticalSection](../Topic/CComMultiThreadModelNoCS::CriticalSection.md)|引用选件类 `CComFakeCriticalSection`。|  
|[CComMultiThreadModelNoCS::ThreadModelNoCS](../Topic/CComMultiThreadModelNoCS::ThreadModelNoCS.md)|引用选件类 `CComMultiThreadModelNoCS`。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CComMultiThreadModelNoCS::Decrement](../Topic/CComMultiThreadModelNoCS::Decrement.md)|\(静态\)递减指定变量的值以线程安全的方式。|  
|[CComMultiThreadModelNoCS::Increment](../Topic/CComMultiThreadModelNoCS::Increment.md)|\(静态\)添加指定的变量的值以线程安全的方式。|  
  
## 备注  
 `CComMultiThreadModelNoCS` 类似于 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 因为它用于递增和递减变量提供线程安全的方法。  但是，那么，当您通过 `CComMultiThreadModelNoCS`引用临界区选件类，方法要么例如 `Lock` 和 `Unlock` 不执行任何操作。  
  
 通常，通过 `ThreadModelNoCS``typedef` 名称使用 `CComMultiThreadModelNoCS`。  此 `typedef` 在 `CComMultiThreadModelNoCS`、 `CComMultiThreadModel`和 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)定义。  
  
> [!NOTE]
>  全局 `typedef` 名称 [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 和 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md) 不引用 `CComMultiThreadModelNoCS`。  
  
 除了 `ThreadModelNoCS`外，`CComMultiThreadModelNoCS` 定义 `AutoCriticalSection` 和 `CriticalSection`。  后面这两个 `typedef` 名称引用 [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，提供空方法与获取和释放临界区。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)