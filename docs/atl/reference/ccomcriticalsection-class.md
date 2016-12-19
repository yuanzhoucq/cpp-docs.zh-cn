---
title: "CComCriticalSection Class | Microsoft Docs"
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
  - "ATL.CComCriticalSection"
  - "CComCriticalSection"
  - "ATL::CComCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCriticalSection class"
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
caps.latest.revision: 21
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类来获取和释放一临界区对象的所有权的方法。  
  
## 语法  
  
```  
  
class CComCriticalSection  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComCriticalSection::CComCriticalSection](../Topic/CComCriticalSection::CComCriticalSection.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComCriticalSection::Init](../Topic/CComCriticalSection::Init.md)|创建和初始化一临界区对象。|  
|[CComCriticalSection::Lock](../Topic/CComCriticalSection::Lock.md)|获取临界区对象的所有权。|  
|[CComCriticalSection::Term](../Topic/CComCriticalSection::Term.md)|释放临界区对象使用的系统资源。|  
|[CComCriticalSection::Unlock](../Topic/CComCriticalSection::Unlock.md)|释放临界区对象的所有权。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComCriticalSection::m\_sec](../Topic/CComCriticalSection::m_sec.md)|**CRITICAL\_SECTION** 对象。|  
  
## 备注  
 `CComCriticalSection` 类似的类别 [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)，除此之外，您必须显式初始化和释放临界区。  
  
 通常，通过 `typedef` 名称 [CriticalSection](../Topic/CComMultiThreadModel::CriticalSection.md)使用 `CComCriticalSection`。  当使用时，此名称引用 `CComCriticalSection`[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。  
  
 比直接调用 `Lock` 和 `Unlock` 参见 [CComCritSecLock选件类](../../atl/reference/ccomcritseclock-class.md) 以一种较为安全的方式使用此选件类。  
  
## 要求  
 **Header:** atlcore.h  
  
## 请参阅  
 [CComFakeCriticalSection Class](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComCritSecLock Class](../../atl/reference/ccomcritseclock-class.md)