---
title: "_bstr_t::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_bstr_t::Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach 方法"
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _bstr_t::Attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将 `BSTR` 包装器链接到 `_bstr_t`。  
  
## 语法  
  
```  
  
      void Attach(  
   BSTR s  
);  
```  
  
#### 参数  
 *s*  
 要与之关联或分配到的 `BSTR`，即 `_bstr_t` 变量。  
  
## 备注  
 如果 `_bstr_t` 以前被附加到了另一个 `BSTR`，并且没有其他 `_bstr_t` 变量使用 `BSTR`，`_bstr_t` 将清理 `BSTR` 资源。  
  
## 示例  
 有关使用 **Attach** 的示例，请参阅 [\_bstr\_t::Assign](../cpp/bstr-t-assign.md)。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_bstr\_t 类](../cpp/bstr-t-class.md)