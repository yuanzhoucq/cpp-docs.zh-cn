---
title: "switch 语句 (C++) | Microsoft Docs"
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
  - "default"
  - "default_cpp"
  - "switch"
  - "switch_cpp"
  - "case"
  - "case_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "case 关键字 [C++], 在 switch 语句中"
  - "default 关键字 [C++]"
  - "switch 关键字 [C++]"
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# switch 语句 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

允许根据整型表达式的值在多个代码段中进行选择。  
  
## 语法  
  
```  
  
      switch ( expression )  
   case constant-expression : statement  
   [default  : statement]  
```  
  
## 备注  
 *expression* 必须属于整型或存在到整型的明确转换的类类型。  将按照[整型提升](../misc/integral-promotions.md)中所述的方式执行整型提升。  
  
 `switch` 语句体由一系列 **case** 标签和一个可选 **default** 标签组成。  **case** 语句中的两个常量表达式的计算结果不能为同一个值。  **default** 标签只能出现一次。  标记语句不是语法要求，但如果它们不存在，`switch` 语句是无意义的。默认语句无需显示在末尾；它可以显示在 switch 语句体的任何位置。  case 或 default 标签只能显示在 switch 语句内。  
  
 每个 **case** 标签中的 *constant\-expression* 将转换为 *expression* 类型，并将与 *expression* 比较是否等效。  控制到其 **case** *constant\-expression* 与 *expression* 的值匹配的语句的传递。  下表中显示了生成的行为。  
  
### switch 语句行为  
  
|条件|操作|  
|--------|--------|  
|转换后的值与提升的控制表达式的值匹配。|控制将转移到跟在该标签后面的语句。|  
|没有常量与 **case** 标签中的常量匹配；**default** 标签存在。|控制将转移到 **default** 标签。|  
|没有常量与 **case** 标签中的常量匹配；**default** 标签不存在。|控制将转移到 `switch` 语句之后的语句。|  
  
 如果找到匹配的表达式，则后续 **case** 或 **default** 标签不会妨碍控制。  [break](../cpp/break-statement-cpp.md) 语句用于停止执行并将控制转移到 `switch` 语句之后的语句。  如果没有 **break** 语句，则将执行从匹配的 **case** 标签到 `switch` 末尾的每个语句，包括 **default**。  例如：  
  
```  
// switch_statement1.cpp  
#include <stdio.h>  
  
int main() {  
   char *buffer = "Any character stream";  
   int capa, lettera, nota;  
   char c;  
   capa = lettera = nota = 0;  
  
   while ( c = *buffer++ )   // Walks buffer until NULL  
   {  
      switch ( c )  
      {  
         case 'A':  
            capa++;  
            break;  
         case 'a':  
            lettera++;  
            break;  
         default:  
            nota++;  
      }  
   }  
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",  
      capa, lettera, (capa + lettera + nota) );  
}  
```  
  
 在上面的示例中，如果 `c` 是大写 `A`，则 `capa` 将递增。  `capa++` 之后的 `break` 语句会终止 `switch` 语句体的执行并将控制转移到 `while` 循环。  如果没有 `break` 语句，`lettera` 和 `nota` 也将递增。  `case 'a'` 的 `break` 语句也能达到类似的目的。  如果 `c` 是小写 `a`，则 `lettera` 将递增，并且 `break` 语句将终止 `switch` 语句体。  如果 `c` 不是 `a` 或 `A`，则将执行 `default` 语句。  
  
 `switch` 语句的内部块可以包含带有初始化的定义，前提是可以访问到它们 \- 即，所有可能的执行路径都不会绕过它们。  使用这些声明引入的名称具有局部范围。  例如：  
  
```  
// switch_statement2.cpp  
// C2360 expected  
#include <iostream>  
using namespace std;  
int main(int argc, char *argv[])  
{  
   switch( tolower( *argv[1] ) )  
   {  
       // Error. Unreachable declaration.  
       char szChEntered[] = "Character entered was: ";  
  
   case 'a' :  
       {  
       // Declaration of szChEntered OK. Local scope.  
       char szChEntered[] = "Character entered was: ";  
       cout << szChEntered << "a\n";  
       }  
       break;  
  
   case 'b' :  
       // Value of szChEntered undefined.  
       cout << szChEntered << "b\n";  
       break;  
  
   default:  
       // Value of szChEntered undefined.  
       cout << szChEntered << "neither a nor b\n";  
       break;  
   }  
}  
```  
  
 `switch` 语句可以嵌套。  在这种情况下，**case** 或 **default** 标签将与封装它们的最近的 `switch` 语句关联。  
  
## Microsoft 专用  
 Microsoft C 未限制 `switch` 语句中 case 值的数量。  该数量仅受可用内存的限制。  ANSI C 要求 `switch` 语句内至少允许使用 257 个 case 标签。  
  
 Microsoft C 的默认设置是启用 Microsoft 扩展。  请使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) 编译器选项禁用这些扩展。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [选择语句](../cpp/selection-statements-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [\(NOTINBUILD\) Using Labels in the case Statement](http://msdn.microsoft.com/zh-cn/a6ff057d-1aee-42ed-a28d-ee6a565b3197)