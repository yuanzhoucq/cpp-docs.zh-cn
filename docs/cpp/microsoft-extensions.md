---
title: "Microsoft 扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Microsoft C/C++ 扩展"
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Microsoft 扩展
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*asm\-statement*:  
 **\_\_asm**  *assembly\-instruction* **;** opt  
  
 **\_\_asm {**  *assembly\-instruction\-list*  **};** opt  
  
 *assembly\-instruction\-list*:  
 *assembly\-instruction* **;** opt  
  
 *assembly\-instruction* **;** *assembly\-instruction\-list* **;** opt  
  
 *ms\-modifier\-list*:  
 *ms\-modifier ms\-modifier\-list* opt  
  
 *ms\-modifier*:  
 **\_\_cdecl**  
  
 **\_\_fastcall**  
  
 **\_\_stdcall**  
  
 **\_\_syscall**（为将来的实现保留）  
  
 **\_\_oldcall**（为将来的实现保留）  
  
 **\_\_unaligned**（为将来的实现保留）  
  
 *based\-modifier*  
  
 *based\-modifier*:  
 **\_\_based \(** *based\-type* **\)**  
  
 *based\-type*:  
 *name*  
  
## 请参阅  
 [语法摘要](../misc/grammar-summary-cpp.md)