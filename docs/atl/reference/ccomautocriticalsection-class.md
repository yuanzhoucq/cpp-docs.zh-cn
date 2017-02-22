---
title: "CComAutoCriticalSection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComAutoCriticalSection"
  - "ATL::CComAutoCriticalSection"
  - "CComAutoCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAutoCriticalSection class"
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComAutoCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComAutoCriticalSection` 来获取和释放一临界区对象的所有权的方法。  
  
## 语法  
  
```  
  
class CComAutoCriticalSection : public CComCriticalSection  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComAutoCriticalSection::CComAutoCriticalSection](../Topic/CComAutoCriticalSection::CComAutoCriticalSection.md)|构造函数。|  
|[CComAutoCriticalSection::~CComAutoCriticalSection](../Topic/CComAutoCriticalSection::~CComAutoCriticalSection.md)|该析构函数。|  
  
## 备注  
 `CComAutoCriticalSection` 类似的类别 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)，除此之外，`CComAutoCriticalSection` 自动初始化在构造函数的临界区对象。  
  
 通常，通过 `typedef` 名称 [AutoCriticalSection](../Topic/CComMultiThreadModel::AutoCriticalSection.md)使用 `CComAutoCriticalSection`。  当使用时，此名称引用 `CComAutoCriticalSection`[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。  
  
 在使用此选件类时，从 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 的 `Init` 和 `Term` 方法不可用。  
  
## 继承层次结构  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComAutoCriticalSection`  
  
## 要求  
 **Header:** atlcore.h  
  
## 请参阅  
 [CComFakeCriticalSection Class](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)