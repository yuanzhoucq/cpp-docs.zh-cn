---
title: "编译器错误 C2689 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2689"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2689"
ms.assetid: b5216fba-524d-4194-9168-26e9dc5210ce
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2689
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 不能在局部类中定义友元函数  
  
 可以在局部类中声明友元函数，但不可以定义它。  
  
 下面的示例生成 C2689：  
  
```  
// C2689.cpp  
// compile with: /c  
void g() {  
   void f2();  
   class X {  
      friend void f2(){}   // C2689  
      friend void f2();   // OK  
   };  
}  
```