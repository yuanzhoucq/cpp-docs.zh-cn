---
title: "编译器错误 C2511 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2511"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2511"
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2511
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”:“class”中没有找到重载的成员函数  
  
 该函数的版本都不是用指定的参数声明的。可能的原因：  
  
1.  传递给函数错误的参数。  
  
2.  以错误的顺序传递参数。  
  
3.  参数名的错误拼写。  
  
 下面的示例生成 C2511：  
  
```  
// C2511.cpp  
// compile with: /c  
class C {  
   int c_2;  
   int Func(char *, char *);  
};  
  
int C::Func(char *, char *, int i) {   // C2511  
// try the following line instead  
// int C::Func(char *, char *) {  
   return 0;  
}  
```