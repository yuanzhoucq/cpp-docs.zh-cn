---
title: "do-while 语句 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "do-while_cpp"
  - "do-while"
  - "do"
  - "while_cpp"
  - "do_cpp"
  - "while"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "do 关键字 [C++]"
  - "do 关键字 [C++], do-while"
  - "do-while 关键字 [C++]"
  - "while 关键字 [C++], do-while"
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# do-while 语句 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

反复执行 *statement*，直到指定的终止条件 \(*expression*\) 的计算结果为零。  
  
## 语法  
  
```  
  
      do  
   statement  
   while ( expression ) ;  
```  
  
## 备注  
 终止条件的测试将在每次执行循环后进行；因此 `do-while` 循环将执行一次或多次，具体取决于终止表达式的值。  `do-while` 语句还可在语句体中执行 [break](../cpp/break-statement-cpp.md)、[goto](../cpp/goto-statement-cpp.md) 或 [return](../cpp/return-statement-cpp.md) 语句时终止。  
  
 *expression* 必须具有算法或指针类型。  执行过程如下所示：  
  
1.  执行语句体。  
  
2.  接着，计算 *expression*。  如果 *expression* 为 false，则 `do-while` 语句将终止，控制将传递到程序中的下一条语句。  如果 *expression* 为 true（非零），则将从第一步开始重复此过程。  
  
## 示例  
 以下示例演示了 `do-while` 语句：  
  
```  
// do_while_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        printf_s("\n%d",i++);  
    } while (i < 3);  
}  
```  
  
## 请参阅  
 [迭代语句](../cpp/iteration-statements-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [While 语句 \(C\+\+\)](../cpp/while-statement-cpp.md)   
 [for 语句 \(C\+\+\)](../cpp/for-statement-cpp.md)   
 [基于范围的 for 语句 \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)