---
title: "while 语句 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: while_cpp
dev_langs: C++
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4b076a1679bec8de9407d253d233e96060aaef4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="while-statement-c"></a>While 语句 (C++)
执行*语句*重复直到*表达式*计算结果为零。  
  
## <a name="syntax"></a>语法  
  
```  
  
      while ( expression )  
   statement  
```  
  
## <a name="remarks"></a>备注  
 测试*表达式*发生在每次执行循环; 因此，`while`循环将执行零次或多次。 *表达式*必须是整数类型、 指针类型，或明确转换为整数的类类型或指针类型。  
  
 A`while`时，还可以终止循环[中断](../cpp/break-statement-cpp.md)， [goto](../cpp/goto-statement-cpp.md)，或[返回](../cpp/return-statement-cpp.md)语句内执行主体。 使用[继续](../cpp/continue-statement-cpp.md)终止当前迭代，但不退出`while`循环。 **继续**将控制权传递给下一个迭代的`while`循环。  
  
 下面的代码使用`while`循环要修剪尾随下划线从字符串：  
  
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
  
 终止条件在循环的顶部。 如果不有任何尾随下划线，则循环将永远不会执行。  
  
## <a name="see-also"></a>另请参阅  
 [迭代语句](../cpp/iteration-statements-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [do-while 语句 (C++)](../cpp/do-while-statement-cpp.md)   
 [for 语句 (C++)](../cpp/for-statement-cpp.md)   
 [基于范围的 for 语句 (C++)](../cpp/range-based-for-statement-cpp.md)