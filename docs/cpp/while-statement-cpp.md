---
title: "While 语句 (C++) | Microsoft Docs"
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
  - "while_cpp"
  - "while"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "while 关键字 [C++]"
  - "while 关键字 [C++], 语法"
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# While 语句 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

重复执行*语句*，直到*表达式*计算为零。  
  
## 语法  
  
```  
  
      while ( expression )  
   statement  
```  
  
## 备注  
 *expression* 的测试在每次执行循环前发生；因此 `while` 循环执行零次或更多次。  *表达式*必须是整型、指针类型或包含明确的整型或指针类型转换的类类型。  
  
 当[中断](../cpp/break-statement-cpp.md)、[导航](../cpp/goto-statement-cpp.md)或[回归](../cpp/return-statement-cpp.md)在语句体中执行时，也可以中止`while` 循环。  请使用[continue](../cpp/continue-statement-cpp.md)语句来结束当前迭代但不退出`while`循环。   **继续**  将控件传递给下一轮循环 `while`。  
  
 以下代码使用 `while` 循环从字符串中剪裁尾随下划线：  
  
```  
// while_statement.cpp  
  
#include <string.h>  
#include <stdio.h>  
char *trim( char *szSource )  
{  
    char *pszEOS = 0;  
  
    //  Set pointer to character before terminating NULL  
    pszEOS = szSource + strlen( szSource ) - 1;  
  
    //  iterate backwards until non '_' is found   
    while( (pszEOS >= szSource) && (*pszEOS == '_') )  
        *pszEOS-- = '\0';  
  
    return szSource;  
}  
int main()  
{  
    char szbuf[] = "12345_____";  
  
    printf_s("\nBefore trim: %s", szbuf);  
    printf_s("\nAfter trim: %s\n", trim(szbuf));  
}  
```  
  
 在循环顶部计算终止条件。  如果没有尾随下划线，循环不执行。  
  
## 请参阅  
 [迭代语句](../cpp/iteration-statements-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [do\-while 语句 \(C\+\+\)](../cpp/do-while-statement-cpp.md)   
 [for 语句 \(C\+\+\)](../cpp/for-statement-cpp.md)   
 [基于范围的 for 语句 \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)