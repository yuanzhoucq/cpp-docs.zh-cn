---
title: "使用没有 () 的函数名不产生代码 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函数 [C++], 没有括号"
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用没有 () 的函数名不产生代码
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当使用在程序中声明并且没有括号的函数名时，编译器不产生代码。  因为编译器计算函数地址，所以不论函数是否有参数，都会出现这样情况；然而，由于不存在函数调用运算符“\(\)”，所以没有调用。  该结果类似于下面这样：  
  
```  
// compile with /Wall to generate a warning  
int a;  
a;      // no code generated here either  
```  
  
 在 Visual C\+\+ 中，甚至使用警告等级 4 也不生成诊断输出。  不发出警告；不产生代码。  
  
 下面的代码示例没有错误地正确编译（有警告）和链接，但是在 `funcn( )` 引用中不产生代码。  为使这正确工作，添加函数调用运算符“\(\)”。  
  
```  
#include <stdio.h>  
void funcn();  
  
int main() {  
   funcn;      /* missing function call operator;   
                  call will fail.  Use funcn() */  
   }  
  
void funcn() {  
   printf("\nHello World\n");  
}  
```  
  
## 请参阅  
 [优化代码](../../build/reference/optimizing-your-code.md)