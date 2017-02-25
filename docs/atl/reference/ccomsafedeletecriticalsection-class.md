---
title: "CComSafeDeleteCriticalSection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComSafeDeleteCriticalSection"
  - "ATL::CComSafeDeleteCriticalSection"
  - "ATL.CComSafeDeleteCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSafeDeleteCriticalSection class"
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CComSafeDeleteCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类来获取和释放一临界区对象的所有权的方法。  
  
## 语法  
  
```  
  
class CComSafeDeleteCriticalSection : public CComCriticalSection  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](../Topic/CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection.md)|构造函数。|  
|[CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection](../Topic/CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComSafeDeleteCriticalSection::Init](../Topic/CComSafeDeleteCriticalSection::Init.md)|创建和初始化一临界区对象。|  
|[CComSafeDeleteCriticalSection::Lock](../Topic/CComSafeDeleteCriticalSection::Lock.md)|获取临界区对象的所有权。|  
|[CComSafeDeleteCriticalSection::Term](../Topic/CComSafeDeleteCriticalSection::Term.md)|释放临界区对象使用的系统资源。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_bInitialized](../Topic/CComSafeDeleteCriticalSection::m_bInitialized.md)|标志内部 **CRITICAL\_SECTION** 对象是否已初始化。|  
  
## 备注  
 `CComSafeDeleteCriticalSection` 从选件类 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)派生。  但是，`CComSafeDeleteCriticalSection` 提供在 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)的其他安全机制。  
  
 当 `CComSafeDeleteCriticalSection` 实例超出范围或从内存中显式删除，基础临界区对象将被自动清理，如果它是有效的。  此外，在中，如果基础临界区对象从内存，未分配还尚未释放 [CComSafeDeleteCriticalSection::Term](../Topic/CComSafeDeleteCriticalSection::Term.md) 方法将正常退出。  
  
 请参见 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 有关临界区帮助器选件类的更多信息。  
  
## 继承层次结构  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComSafeDeleteCriticalSection`  
  
## 要求  
 **Header:** atlcore.h  
  
## 请参阅  
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)