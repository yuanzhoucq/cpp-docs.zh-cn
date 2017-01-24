---
title: "CComCritSecLock Class | Microsoft Docs"
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
  - "ATL::CComCritSecLock"
  - "ATL.CComCritSecLock<TLock>"
  - "ATL::CComCritSecLock<TLock>"
  - "ATL.CComCritSecLock"
  - "CComCritSecLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCritSecLock class"
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComCritSecLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为锁定和取消锁定临界区对象的方法。  
  
## 语法  
  
```  
  
      template<  
   class TLock  
> class CComCritSecLock  
```  
  
#### 参数  
 *TLock*  
 要锁定和取消锁定的对象。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CComCritSecLock::CComCritSecLock](../Topic/CComCritSecLock::CComCritSecLock.md)|构造函数。|  
|[CComCritSecLock::~CComCritSecLock](../Topic/CComCritSecLock::~CComCritSecLock.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CComCritSecLock::Lock](../Topic/CComCritSecLock::Lock.md)|调用此方法锁定临界区对象。|  
|[CComCritSecLock::Unlock](../Topic/CComCritSecLock::Unlock.md)|调用此方法以打开临界区对象。|  
  
## 备注  
 使用此选件类用于锁定和取消锁定该对象的一种较为安全的方法与具有 [CComCriticalSection选件类](../../atl/reference/ccomcriticalsection-class.md) 或 [CComAutoCriticalSection选件类](../../atl/reference/ccomautocriticalsection-class.md)。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [CComAutoCriticalSection Class](../../atl/reference/ccomautocriticalsection-class.md)