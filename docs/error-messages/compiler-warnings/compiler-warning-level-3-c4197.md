---
title: "编译器警告（等级 3）C4197 | Microsoft Docs"
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
  - "C4197"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4197"
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4197
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 忽略转换中的顶级 volatile 变量  
  
 编译器检测到向由 [volatile](../../cpp/volatile-cpp.md) 限定的 R\-值类型的转换，或从 R\-值类型向由变量限定的某种类型的转换。  根据 C 标准 \(6.5.3\)，与限定类型相关的属性只对左值表达式有意义。  
  
 下面的示例生成 C4197：  
  
```  
// C4197.cpp  
// compile with: /W3  
#include <stdio.h>  
#include <signal.h>  
#include <stdlib.h>  
  
void sigproc(int);  
struct S  
{  
   int i;  
} s;  
  
int main()  
{  
   signal(SIGINT, sigproc);  
   s.i = 1;  
   S *pS = &s;  
   for ( ; (volatile int)pS->i ; )   // C4197  
      break;  
   // for ( ; *(volatile int *)&pS->i ; )   // OK  
   //    break;  
}  
  
void sigproc(int) // ctrl-C  
{  
   signal(SIGINT, sigproc);  
   s.i = 0;  
}  
  
```