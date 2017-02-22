---
title: "CComObjectNoLock Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComObjectNoLock"
  - "ATL::CComObjectNoLock"
  - "ATL.CComObjectNoLock<Base>"
  - "CComObjectNoLock"
  - "ATL::CComObjectNoLock<Base>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectNoLock class"
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComObjectNoLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现一nonaggregated对象的 **IUnknown**，但是，不会使在构造函数的模块锁计数。  
  
## 语法  
  
```  
  
      template<  
   class Base   
>  
class CComObjectNoLock :  
   public Base  
```  
  
#### 参数  
 `Base`  
 您的选件类，从派生 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及从其他接口包含在对象若要支持。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CComObjectNoLock::CComObjectNoLock](../Topic/CComObjectNoLock::CComObjectNoLock.md)|构造函数。|  
|[CComObjectNoLock::~CComObjectNoLock](../Topic/CComObjectNoLock::~CComObjectNoLock.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CComObjectNoLock::AddRef](../Topic/CComObjectNoLock::AddRef.md)|递增对象的引用计数。|  
|[CComObjectNoLock::QueryInterface](../Topic/CComObjectNoLock::QueryInterface.md)|返回指向请求的接口。|  
|[CComObjectNoLock::Release](../Topic/CComObjectNoLock::Release.md)|在递减对象的引用计数。|  
  
## 备注  
 `CComObjectNoLock` 类似于 [CComObject](../../atl/reference/ccomobject-class.md) 因为它实现了nonaggregated对象的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) ;但是，`CComObjectNoLock` 不会使在构造函数的模块锁计数。  
  
 ATL使用 `CComObjectNoLock` 在内部用于选件类工厂。  通常，您不需要直接使用此选件类。  
  
## 继承层次结构  
 `Base`  
  
 `CComObjectNoLock`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)