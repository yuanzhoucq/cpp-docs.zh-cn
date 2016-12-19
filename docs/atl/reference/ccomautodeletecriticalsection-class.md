---
title: "CComAutoDeleteCriticalSection Class | Microsoft Docs"
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
  - "ATL.CComAutoDeleteCriticalSection"
  - "CComAutoDeleteCriticalSection"
  - "ATL::CComAutoDeleteCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAutoDeleteCriticalSection class"
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComAutoDeleteCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类来获取和释放一临界区对象的所有权的方法。  
  
## 语法  
  
```  
  
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection  
  
```  
  
## 备注  
 `CComAutoDeleteCriticalSection` 从选件类 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)派生。  但是，`CComAutoDeleteCriticalSection` 重写 [术语](../Topic/CComSafeDeleteCriticalSection::Term.md) 方法以 `private` 访问，强制内部内存进行清理，只有当此选件类实例超出范围或从内存时显式删除。  
  
 此选件类不会在其基类的其他方法。  请参见 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) 和 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 有关临界区帮助器选件类的更多信息。  
  
## 继承层次结构  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## 要求  
 **Header:** atlcore.h  
  
## 请参阅  
 [CComSafeDeleteCriticalSection Class](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)