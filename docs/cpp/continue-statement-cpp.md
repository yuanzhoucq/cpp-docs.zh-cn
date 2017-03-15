---
title: "continue 语句 (C++) | Microsoft Docs"
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
  - "continue"
  - "continue_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "continue 关键字 [C++]"
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# continue 语句 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

强制转移对最小封闭 [do](../cpp/do-while-statement-cpp.md)、[for](../cpp/for-statement-cpp.md) 或 [while](../cpp/while-statement-cpp.md) 循环的控制表达式的控制。  
  
## 语法  
  
```  
continue;  
```  
  
## 备注  
 将不会执行当前迭代中的所有剩余语句。  确定循环的下一次迭代，如下所示：  
  
-   在 `do` 或 `while` 循环中，下一个迭代首先会重新计算 `do` 或 `while` 语句的控制表达式。  
  
-   在 `for` 循环中（使用语法 `for`\(`init-expr`; `cond-expr`; `loop-expr`\)），将执行 `loop-expr` 子句。  然后，重新计算 `cond-expr` 子句，并根据结果确定该循环结束还是进行另一个迭代。  
  
 下面的示例演示了如何使用 `continue` 语句跳过代码部分并启动循环的下一个迭代。  
  
## 示例  
  
```  
// continue_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        i++;  
        printf_s("before the continue\n");  
        continue;  
        printf("after the continue, should never print\n");  
     } while (i < 3);  
  
     printf_s("after the do loop\n");  
}  
```  
  
  **在继续之前**  
**在继续之前**  
**在继续之前**  
**在 do 循环之后**   
## 请参阅  
 [跳转语句](../cpp/jump-statements-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)