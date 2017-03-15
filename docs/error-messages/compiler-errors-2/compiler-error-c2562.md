---
title: "编译器错误 C2562 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2562"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2562"
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2562
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: “void”函数返回值  
  
 该函数被声明为 `void`，但返回一个值。  
  
 不正确的函数原型可能导致此错误。  
  
 如果在函数声明中指定返回类型，可以修复此错误。  
  
 下面的示例生成 C2562：  
  
```  
// C2562.cpp  
// compile with: /c  
void testfunc() {  
   int i;  
   return i;   // C2562 delete the return to resolve  
}  
```