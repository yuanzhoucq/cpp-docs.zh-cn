---
title: "_bstr_t::GetBSTR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "GetBSTR"
  - "_bstr_t::GetBSTR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBSTR 方法"
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _bstr_t::GetBSTR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 指向 `_bstr_t` 包装的 `BSTR` 的开头。  
  
## 语法  
  
```  
  
BSTR& GetBSTR( );  
  
```  
  
## 返回值  
 `_bstr_t` 包装的 `BSTR` 的开头。  
  
## 备注  
 `GetBSTR` 影响所有共享 `BSTR` 的 `_bstr_t` 对象。  多个 `_bstr_t` 可以通过使用复制构造函数和 `operator=` 共享 `BSTR`。  
  
## 示例  
 有关使用 `GetBSTR` 的示例，请参阅 [\_bstr\_t::Assign](../cpp/bstr-t-assign.md)。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_bstr\_t 类](../cpp/bstr-t-class.md)