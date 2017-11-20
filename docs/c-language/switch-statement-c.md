---
title: "switch 语句 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: switch
dev_langs: C++
helpviewer_keywords: switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b66e9f40e3fb7f4c9a6c9f6fcb9bcd9c2a45fdd3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="switch-statement-c"></a>switch 语句 (C)
`switch` 和 **case** 语句帮助控制复杂条件和分支运算。 `switch` 语句将控制权转交给其主体中的语句。  
  
## <a name="syntax"></a>语法  
 *selection-statement*:  
 **switch (** *expression* **)** *statement*  
  
 *labeled-statement*:  
 **case**  *constant-expression*  **:**  *statement*  
  
 **default :**  *statement*  
  
 控制权将传递给其 **case** *constant-expression* 与 **switch (** *expression* **)** 的值匹配的语句。 `switch` 语句可以包含任意数量的 **case** 实例，但同一 `switch` 语句中的两个 case 常量不能具有相同的值。 语句体的执行从选定语句处开始并继续，直到该主体的结尾或直到 **break** 语句将控制权传出主体。  
  
 `switch` 语句的使用通常类似于：  
  
 `switch` ( *expression* )  
  
 **{**  
  
 *declarations*  
  
 .  
  
 .  
  
 .  
  
 **case** *constant-expression* **:**  
  
 *statements executed if the expression equals the*  
  
 *value of this constant-expression*  
  
 .  
  
 .  
  
 .  
  
 **break;**  
  
 **default :**  
  
 *statements executed if expression does not equal*  
  
 *any case constant-expression*  
  
 **}**  
  
 可以使用 **break** 语句结束 `switch` 语句中特定用例的处理并分支到 `switch` 语句的末尾。 如果不使用 **break**，则程序会继续到下一用例，并执行语句，直到达到 **break** 或该语句的末尾。 在某些情况下，可能需要此继续符。  
  
 如果任何 **case** *constant-expression* 均不等于**switch (** *expression* **)** 的值，则会执行 **default** 语句。 如果省略 **default** 语句且未找到任何 **case** 匹配项，则不会执行 `switch` 主体中的任何语句。 最多可以有一个 **default** 语句。 **default** 语句无需显示在末尾；它可以显示在 `switch` 语句主体中的任何位置。 **case** 或 **default** 标签只能显示在 `switch` 语句内部。  
  
 `switch` *expression* 和 **case** *constant-expression* 的类型必须是整型。 每个 **case** *constant-expression* 的值在语句体中必须唯一。  
  
 `switch` 语句体的 **case** 和 **default** 标签只在初始测试中有意义，该测试将确定语句体中开始执行的位置。 Switch 语句可以嵌套。 在执行到任何 `switch` 语句中之前，将初始化所有静态变量。  
  
> [!NOTE]
>  声明可以出现在构成 `switch` 主体的复合语句的前面，但不执行包含在声明中的初始化。 `switch` 语句将控制权直接转交给主体中的一个可执行语句，并绕过包含初始化的行。  
  
 下面的示例阐释了 `switch` 语句：  
  
```  
switch( c )   
{  
    case 'A':  
        capa++;  
    case 'a':  
        lettera++;  
    default :  
        total++;  
}  
```  
  
 如果 `c` 等于 `'A'`，则会执行此示例中的 `switch` 主体的所有三个语句，因为不会在以下用例前显示 **break** 语句。 将执行控制转交给第一个语句 (`capa++;`) 并继续按顺序转交给主体的其余部分。 如果 `c` 等于 `'a'`，则 `lettera` 和 `total` 将增加。 如果 `total` 不等于 `c` 或 `'A'`，则仅 `'a'` 增加。  
  
```  
switch( i )   
{  
    case -1:  
        n++;  
        break;  
    case 0 :  
        z++;  
        break;  
    case 1 :  
        p++;  
        break;  
}  
```  
  
 在此示例中，**break** 语句跟在 `switch` 主体的每个语句的后面。 在执行一个语句后，**break** 语句将强制从语句体中退出。 如果 `i` 等于 -1，则仅 `n` 将增加。 `n++;` 语句后面的 **break** 会导致执行控制传递出语句体，并绕过剩余语句。 同样，如果 `i` 等于 0，则仅 `z` 将增加；如果 `i` 等于 1，则仅 `p` 将增加。 从严格意义上讲，最后的 **break** 语句不是必需的，因为控制权将在复合语句的结尾传递出语句体，但将包含它以获得一致性。  
  
 如下面的示例所示，一个语句可以包含多个 **case** 标签：  
  
```  
case 'a' :  
case 'b' :  
case 'c' :  
case 'd' :  
case 'e' :  
case 'f' :  hexcvt(c);  
```  
  
 在此示例中，如果 *constant-expression* 等于 `'a'` 和 `'f'` 之间的任何字母，则调用 `hexcvt` 函数。  
  
 **Microsoft 专用**  
  
 Microsoft C 未限制 `switch` 语句中 case 值的数量。 该数量仅受可用内存的限制。 ANSI C 要求 `switch` 语句内至少允许使用 257 个 case 标签。  
  
 Microsoft C 的默认设置是启用 Microsoft 扩展。 使用 /Za 编译器选项禁用这些扩展。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [switch 语句 (C++)](../cpp/switch-statement-cpp.md)