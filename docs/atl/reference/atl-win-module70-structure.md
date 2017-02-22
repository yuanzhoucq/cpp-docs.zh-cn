---
title: "_ATL_WIN_MODULE70 Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ATL_WIN_MODULE70"
  - "ATL::_ATL_WIN_MODULE70"
  - "ATL._ATL_WIN_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_WIN_MODULE70 structure"
  - "ATL_WIN_MODULE70 structure"
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# _ATL_WIN_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用由多窗口代码在ATL。  
  
## 语法  
  
```  
  
      struct _ATL_WIN_MODULE70{  
   UNIT cbSize;  
   CRITICAL_SECTION m_csWindowCreate;  
   _AtlCreateWndData* m_pCreateWndList;  
   CSimpleArray<ATOM> m_rgWindowClassAtoms;  
};  
```  
  
## 成员  
 `cbSize`  
 结构的大小，用于控制。  
  
 `m_csWindowCreate`  
 用于对windows注册代码的访问。  在内部使用由ATL。  
  
 **m\_pCreateWndList**  
 用于将windows到它们的对象。  在内部使用由ATL。  
  
 **m\_rgWindowClassAtoms**  
 用于跟踪窗口选件类注册，以便可以正确中注销在终止。  在内部使用由ATL。  
  
## 备注  
 [\_ATL\_WIN\_MODULE](../Topic/_ATL_WIN_MODULE.md) 定义为 `_ATL_WIN_MODULE70`typedef。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [结构](../../atl/reference/atl-structures.md)