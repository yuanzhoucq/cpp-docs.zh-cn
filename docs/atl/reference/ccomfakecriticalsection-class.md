---
title: "CComFakeCriticalSection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComFakeCriticalSection"
  - "CComFakeCriticalSection"
  - "ATL::CComFakeCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComFakeCriticalSection class"
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComFakeCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类的方法和 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 相同，但不提供临界区。  
  
## 语法  
  
```  
  
class CComFakeCriticalSection  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComFakeCriticalSection::Init](../Topic/CComFakeCriticalSection::Init.md)|因为没有临界区，不执行。|  
|[CComFakeCriticalSection::Lock](../Topic/CComFakeCriticalSection::Lock.md)|因为没有临界区，不执行。|  
|[CComFakeCriticalSection::Term](../Topic/CComFakeCriticalSection::Term.md)|因为没有临界区，不执行。|  
|[CComFakeCriticalSection::Unlock](../Topic/CComFakeCriticalSection::Unlock.md)|因为没有临界区，不执行。|  
  
## 备注  
 `CComFakeCriticalSection` 反射在 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)找到方法。  但是，`CComFakeCriticalSection` 不提供临界区;因此，其方法不执行任何操作。  
  
 通常，通过 `typedef` 名称使用 `CComFakeCriticalSection`，`AutoCriticalSection` 或 `CriticalSection`。  在使用 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) 或 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)时，这两个 `typedef` 名称引用 `CComFakeCriticalSection`。  在使用 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)时，它们引用 [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) 和 `CComCriticalSection`，分别。  
  
## 要求  
 **Header:** atlcore.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)