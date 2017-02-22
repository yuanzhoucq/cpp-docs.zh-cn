---
title: "_bstr_t::GetAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_bstr_t::GetAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetAddress 方法"
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# _bstr_t::GetAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 释放所有现有字符串并返回一个新分配的字符串的地址。  
  
## 语法  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## 返回值  
 指向由 `_bstr_t` 包装的 `BSTR` 的指针。  
  
## 备注  
 `GetAddress` 影响所有共享 `BSTR` 的 `_bstr_t` 对象。  多个 `_bstr_t` 可以通过使用复制构造函数和 `operator=` 共享 `BSTR`。  
  
## 示例  
 有关使用 `GetAddress` 的示例，请参阅 [\_bstr\_t::Assign](../cpp/bstr-t-assign.md)。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_bstr\_t 类](../cpp/bstr-t-class.md)