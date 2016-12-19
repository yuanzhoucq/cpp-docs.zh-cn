---
title: "编译器警告（等级 1）C4807 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4807"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4807"
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4807
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operation”: 类型“type”与类型“type”的有符号位域的混合不安全  
  
 在将一位有符号位域与 `bool` 变量进行比较时生成此警告。 因为一位有符号位域只能包含值 \-1 或 0，所以将其与 `bool` 比较很危险。 将 `bool` 与一位无符号位域进行混合不生成警告，因为它们与 `bool` 相同，只包含 0 或 1。  
  
## 示例  
 下面的示例生成 C4807：  
  
```  
// C4807.cpp // compile with: /W1 typedef struct bitfield { signed mybit : 1; } mybitfield; int main() { mybitfield bf; bool b = true; // try.. // int b = true; bf.mybit = -1; if (b == bf.mybit) {   // C4807 b = false; } }  
```