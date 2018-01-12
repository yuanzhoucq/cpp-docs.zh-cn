---
title: "切换语句 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
dev_langs: C++
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e668756e8cabafbdef522d6754487efe452f96de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="switch-statement-c"></a>switch 语句 (C++)
允许根据整型表达式的值在多个代码段中进行选择。  
  
## <a name="syntax"></a>语法  
  
```  
   switch ( init; expression )  
   case constant-expression : statement  
   [default  : statement]  
```  
  
## <a name="remarks"></a>备注  
 *表达式*必须是整数类型或明确转换为整数类型的类类型。 中所述执行整型提升[标准转换](standard-conversions.md)。  
  
 `switch`语句体由一系列组成**用例**标签和一个可选**默认**标签。 在任何两个常量表达式**用例**语句可以计算为相同的值。 **默认**标签只能出现一次。 标记语句不是语法要求，但如果它们不存在，`switch` 语句是无意义的。   默认语句无需显示在末尾；它可以显示在 switch 语句体的任何位置。 case 或 default 标签只能显示在 switch 语句内。  
  
 *常量表达式*在每个**用例**标签转换为的类型*表达式*和与比较*表达式*为相等性。 控制将传递给其**用例***常量表达式*匹配的值*表达式*。 下表中显示了生成的行为。  
  
### <a name="switch-statement-behavior"></a>switch 语句行为  
  
|条件|操作|  
|---------------|------------|  
|转换后的值与提升的控制表达式的值匹配。|控制将转移到跟在该标签后面的语句。|  
|没有一个常量匹配中的常量**用例**标签;**默认**标签不存在。|控制转移到其中**默认**标签。|  
|没有一个常量匹配中的常量**用例**标签;**默认**标签不存在。|控制将转移到 `switch` 语句之后的语句。|  
  
 如果找到匹配的表达式，则控件不会妨碍后续**用例**或**默认**标签。 [中断](../cpp/break-statement-cpp.md)语句用于停止执行并将控制权转交给之后的语句`switch`语句。 而无需**中断**语句、 从匹配的每个语句**用例**到末尾的标签`switch`，包括**默认**，执行。 例如:  
  
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
  
 在上面的示例中，如果 `capa` 是大写 `c`，则 `A` 将递增。 `break` 之后的 `capa++` 语句会终止 `switch` 语句体的执行并将控制转移到 `while` 循环。 而无需`break`语句中，执行将"贯穿"到下一步的标记语句，以便`lettera`和`nota`也将递增。 `break` 的 `case 'a'` 语句也能达到类似的目的。 如果 `c` 是小写 `a`，则 `lettera` 将递增，并且 `break` 语句将终止 `switch` 语句体。 如果 `c` 不是 `a` 或 `A`，则将执行 `default` 语句。  

 **2017 及更高版本的 visual Studio:** (适用于[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` C + + 17 标准中指定属性。 可在`switch`语句该回退通过行为旨在作为提示编译器 （或任何人阅读代码）。 Visual c + + 编译器当前不会警告 fallthrough 行为，因此此特性没有任何效果编译器行为。 请注意，该属性将应用于标记的语句; 中的空语句换而言之，分号是必需的。

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

 **Visual Studio 2017 15.3 及更高版本**(适用于[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): switch 语句可能引入并初始化其作用域仅限于 switch 语句的块变量：

```cpp
 switch (Gadget gadget(args); auto s = gadget.get_status())
        {
        case status::good:
            gadget.zip();
            break;
        case status::bad:
            throw BadGadget();
        };
```

 `switch` 语句的内部块可以包含带有初始化的定义，前提是可以访问到它们 - 即，所有可能的执行路径都不会绕过它们。 使用这些声明引入的名称具有局部范围。 例如:  
  
```cpp  
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
  
 `switch` 语句可以嵌套。 在这种情况下，**用例**或**默认**标签将与最近关联`switch`封装它们的语句。  

 
## <a name="microsoft-specific"></a>Microsoft 专用  
 Microsoft C 未限制 `switch` 语句中 case 值的数量。 该数量仅受可用内存的限制。 ANSI C 要求 `switch` 语句内至少允许使用 257 个 case 标签。  
  
 Microsoft C 的默认设置是启用 Microsoft 扩展。 使用[/Za](../build/reference/za-ze-disable-language-extensions.md)编译器选项禁用这些扩展。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [选择语句](../cpp/selection-statements-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)   
 