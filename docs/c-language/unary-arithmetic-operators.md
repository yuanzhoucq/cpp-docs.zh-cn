---
title: "一元算术运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C], unary
- tilde (~) one's complement operator
- bitwise-complement operator
- arithmetic operators [C++], unary
- + operator, unary operators
- unary operators
- exclamation points
- ~ operator, one's complement operator
- logical negation
- '! operator, unary arithmetic operators'
ms.assetid: 78c91415-d469-499e-9dfe-4435350fd333
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 875fd5c87583f93a647cf51907d897603f923e7e
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="unary-arithmetic-operators"></a>一元算术运算符
下面的列表中讨论了 C 一元加、算术求反、求补和逻辑求反运算符：  
  
|运算符|说明|  
|--------------|-----------------|  
|**+**|括号内的表达式前面的一元加运算符强制对包含的运算进行分组。 它用于涉及多个结合的或可交换的二元运算符的表达式。 操作数必须具有算法类型。 结果为操作数的值。 整型操作数将进行整型提升。 结果的类型为提升后的操作数的类型。|  
|**-**|算术求反运算符生成其操作数的负值（2 的补数）。 操作数必须是整型值或浮点值。 此运算符执行常用算术转换。|  
|`~`|按位求补（或按位“非”）运算符将产生其操作数的按位补数。 操作数必须为整型。 此运算符执行常用算术转换；结果具有转换后的操作数的类型。|  
|**!**|如果其操作数为 true（非零），则逻辑求反（逻辑“非”）运算符将生成值 0；如果其操作数为 false (0)，则生成值 1。 结果具有 `int` 类型。 操作数必须是整型值、浮点值或指针值。|  
  
 指针上的一元算术运算是非法的。  
  
## <a name="examples"></a>示例  
 下面的示例演示了一元算术运算符：  
  
```  
short x = 987;  
    x = -x;  
```  
  
 在上面的示例中，`x` 的新值为 987 的负数或 -987。  
  
```  
unsigned short y = 0xAAAA;  
    y = ~y;  
```  
  
 在此示例中，赋给 `y` 的新值是无符号值 0xAAAA 或 0x5555 的二进制反码。  
  
```  
if( !(x < y) )  
```  
  
 如果 `x` 大于或等于 `y`，则该表达式的结果为 1 (true)。 如果 `x` 小于 `y`，则结果为 0 (false)。  
  
## <a name="see-also"></a>另请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)
