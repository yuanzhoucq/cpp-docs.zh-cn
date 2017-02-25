---
title: "_AtlCreateWndData Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::_AtlCreateWndData"
  - "ATL._AtlCreateWndData"
  - "_AtlCreateWndData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_AtlCreateWndData structure"
  - "AtlCreateWndData structure"
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# _AtlCreateWndData Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此机制在ATL的多窗口代码包含选件类实例数据。  
  
## 语法  
  
```  
  
      struct _AtlCreateWndData{  
   void* m_pThis;  
   DWORD m_dwThreadID;  
   _AtlCreateWndData* m_pNext;  
};  
```  
  
## 成员  
 **m\_pThis**  
 **this** 使用指针到选件类实例的get访问在窗口过程。  
  
 `m_dwThreadID`  
 当前选件类实例的线程ID。  
  
 **m\_pNext**  
 到下 `_AtlCreateWndData` 对象的指针。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [结构](../../atl/reference/atl-structures.md)