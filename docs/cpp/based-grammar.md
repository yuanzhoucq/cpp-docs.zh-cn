---
title: "__based 语法 | Microsoft Docs"
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
  - "基于寻址"
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# __based 语法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 在需要精确控制将对象分配到的段（基于静态和动态的数据）时，基寻址很有用。  
  
 32 位和 64 位编译中可接受的基寻址的唯一形式是“基于指针”，它定义一个包含针对 32 位或 64 位基的 32 位或 64 位置换或基于 `void`。  
  
## 语法  
 *based\-range\-modifier*:  
 **\_\_based\(**  *base\-expression*  **\)**  
  
 *base\-expression*:  
 *based\-variablebased\-abstract\-declaratorsegment\-namesegment\-cast*  
  
 *based\-variable*:  
 *identifier*  
  
 *based\-abstract\-declarator*:  
 *abstract\-declarator*  
  
 *base\-type*:  
 *type\-name*  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [基指针](../cpp/based-pointers-cpp.md)