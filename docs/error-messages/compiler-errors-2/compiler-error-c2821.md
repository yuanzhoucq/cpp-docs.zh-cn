---
title: "编译器错误 C2821 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2821"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2821"
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2821
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator new”的第一个形参必须为“unsigned int”  
  
 [运算符 new](../Topic/operator%20new%20\(%3Cnew%3E\).md) 的第一个形参必须是无符号 `int`。  
  
 下面的示例生成 C2821：  
  
```  
// C2821.cpp  
// compile with: /c  
void * operator new( /* unsigned int,*/ void * );   // C2821  
void * operator new( unsigned int, void * );  
```