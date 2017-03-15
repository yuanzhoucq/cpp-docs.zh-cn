---
title: "_com_ptr_t::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t::Detach"
  - "_com_ptr_t.Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Detach 方法"
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_ptr_t::Detach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 提取并返回封装的接口指针。  
  
## 语法  
  
```  
  
Interface* Detach( ) throw( );  
  
```  
  
## 备注  
 提取并返回封装的接口指针，然后将封装的指针存储清除为 **NULL**。  这将从封装中移除接口指针。  将由您对返回的接口指针调用 **Release**。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_ptr\_t 类](../cpp/com-ptr-t-class.md)