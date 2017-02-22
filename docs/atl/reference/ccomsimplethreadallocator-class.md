---
title: "CComSimpleThreadAllocator Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComSimpleThreadAllocator"
  - "ATL::CComSimpleThreadAllocator"
  - "ATL.CComSimpleThreadAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL threads"
  - "ATL threads, 分配"
  - "CComSimpleThreadAllocator class"
  - "线程处理 [ATL], selecting threads"
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComSimpleThreadAllocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类管理选件类的 `CComAutoThreadModule`线程选择。  
  
## 语法  
  
```  
  
class CComSimpleThreadAllocator  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComSimpleThreadAllocator::GetThread](../Topic/CComSimpleThreadAllocator::GetThread.md)|选择线程。|  
  
## 备注  
 `CComSimpleThreadAllocator` 管理 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)的线程选择。  `CComSimpleThreadAllocator::GetThread` 通过每个线程循环并返回下一个在序列。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [CComApartment Class](../../atl/reference/ccomapartment-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)