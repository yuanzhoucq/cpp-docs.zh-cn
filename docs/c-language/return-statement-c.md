---
title: "return 语句 (C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "返回语句中的 ( ) 小括号"
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# return 语句 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`return` 语句终止函数的执行并返回对调用函数的控制。  在这种获取权点后执行将恢复。  `return` 语句可以将值返回给调用函数。  有关更多信息，请参见[返回类型](../c-language/return-type.md)。  
  
## 语法  
 *jump\-statement*：  
 **返回**  *表达式*  选项 **;**  
  
 如果表达式存在的话，*expression* 的值将返回到调用函数。  如果 *expression* 省略，该函数回归值未定义。  如果存在表达式，先计算然后再转换到函数返回的类型。  如果用回归类型 `void` 声明函数，包含表达式的 `return` 语句生成警告，并且该表达式不进行计算。  
  
 如果在函数定义中 `return` 语句未出现，在执行被调用函数的最后一个语句后，空间自动返回到调用函数。  在这种情况下，当调用该函数时，返回值将未定义。  如果不需要回归值，声明该函数具有 `void` 返回类型；否则，默认返回类型是 `int`。  
  
 许多程序员使用括号括 `return` 语句的 *表达式* 参数。  但是， C 不需要括号。  
  
 此示例演示 `return` 语句：  
  
```  
#include <limits.h>  
#include <stdio.h>  
  
void draw( int i, long long ll );  
long long sq( int s );  
  
int main()  
{  
    long long y;  
    int x = INT_MAX;  
  
    y = sq( x );  
    draw( x, y );  
    return x;  
}  
  
long long sq( int s )  
{  
    // Note that parentheses around the return expression   
    // are allowed but not required here.  
    return( s * (long long)s );  
}  
  
void draw( int i, long long ll )  
{  
    printf( "i = %d, ll = %lld\n", i, ll );  
    return;  
}  
  
```  
  
 在此示例中，`main` 函数调用两个函数 `sq` 和 `draw`。  `sq` 函数返回 `x * x` 的值为 `main`，在此处返回值分配给给 `y`。  在 `sq` 中返回表达式两边的括号，作为表达式的一部分计算，但返回的报表不需要。  因为表达式它转换为返回类型之前被计算，`sq` 表达式的类型为返回类型以及可能导致意外结果强制转换类型以防止一个可能的整数溢出.  `draw` 函数被声明为 `void` 函数。  它打印参数值，然后返回空语句结束该函数，并不返回值。  尝试赋值 `draw` 的回归值会导致发布诊断信息。  `main` 函数然后返回 `x` 的值赋给操作系统。  
  
 示例的输出如下所示：  
  
  **i \= 2147483647，ll \= 4611686014132420609**   
## 请参阅  
 [语句](../c-language/statements-c.md)