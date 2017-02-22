---
title: "编译器错误 C2142 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2142"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2142"
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2142
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函数声明有差异，只在一个声明中指定了变量参数  
  
 函数的一个声明包含变量参数列表。  而另一个声明不包含。  仅用于 ANSI C \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\)。  
  
 下面的示例生成 C2142：  
  
```  
// C2142.c  
// compile with: /Za /c  
void func();  
void func( int, ... );   // C2142  
void func2( int, ... );   // OK  
```