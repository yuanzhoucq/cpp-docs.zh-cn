---
title: "编译器警告（等级 4）C4460 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4460"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4460"
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 编译器警告（等级 4）C4460
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

WinRT 或 CLR 运算符“operator”具有按引用传递的参数。WinRT 或 CLR 运算符“operator”的语义与 C\+\+ 运算符“operator”的语义不同，是否希望按值传递？  
  
 你通过引用向用户定义的 Windows 运行时或 CLR 运算符传递了一个值。  如果该值在函数内发生更改，则请注意，在函数调用之后返回的值将被赋予函数的返回值。  在标准 C\+\+ 中，更改的值将在函数调用之后得到反映。  
  
## 示例  
 下面的示例生成 C4460，并演示如何修复此错误。  
  
```  
// C4460.cpp  
// compile with: /W4 /clr   
#include <stdio.h>  
  
public value struct V {  
   static V operator ++(V& me) {   // C4460  
   // try the following line instead  
   // static V operator ++(V me) {  
  
      printf_s(__FUNCSIG__ " called\n");  
      V tmp = me;  
      me.m_i++;  
      return tmp;  
   }  
   int m_i;  
};  
  
int main() {  
   V v;  
   v.m_i = 0;  
  
   printf_s("%d\n", v.m_i);   // Should print 0  
   v++;   // Translates to "v = V::operator ++(v)"  
   printf_s("%d\n", v.m_i);   // will print 0, hence the warning  
}  
```