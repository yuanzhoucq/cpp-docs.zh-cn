---
title: "C 逻辑运算符 | Microsoft Docs"
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
- logical operators, expression sequence points
- logical operators, C
- logical AND operator
- '|| operator'
- operators [C], logical
- short-circuit evaluation
- '&& operator'
- logical OR operator
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
caps.latest.revision: 8
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
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 91df7af4322fc3fd8022542ffeb0c6b7b2d2e087
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="c-logical-operators"></a>C 逻辑运算符
逻辑运算符执行逻辑“与”(&&) 和逻辑“或”(`||`) 运算。  
  
 **语法**  
  
 *logical-AND-expression*：  
 *inclusive-OR-expression*  
  
 *logical-AND-expression*  **&&**  *inclusive-OR-expression*  
  
 *logical-OR-expression*:  
 *logical-AND-expression*  
  
 *logical-OR-expression* **| |** *logical-AND-expression*  
  
 逻辑运算符不执行常用算术转换。 相反，它们根据其等效性为 0 计算每个操作数。 逻辑运算的结果不是 0 就是 1。 结果的类型为 `int`。  
  
 C 逻辑运算符如下所述：  
  
|运算符|描述|  
|--------------|-----------------|  
|**&&**|如果两个操作数具有非零值，则逻辑“与”运算符产生值 1。 如果其中一个操作数等于 0，则结果为 0。 如果逻辑“与”运算的第一个操作数等于 0，则不会计算第二个操作数。|  
|`&#124;&#124;`|逻辑“或”运算符对其操作数执行“与或”运算。 如果两个操作数的值均为 0，则结果为 0。 如果其中一个操作数具有非零值，则结果为 1。 如果逻辑“或”运算的第一个操作数具有非零值，则不会计算第二个操作数。|  
  
 逻辑“与”和逻辑“或”表达式的操作数从左到右进行计算。 如果第一个操作数的值足以确定运算的结果，则不会计算第二个操作数。 这称作“短路计算”。 第一个操作数后有一个序列点。 有关详细信息，请参阅[序列点](../c-language/c-sequence-points.md)。  
  
## <a name="examples"></a>示例  
 下面的示例演示了逻辑运算符：  
  
```  
int w, x, y, z;  
  
if ( x < y && y < z )  
    printf( "x is less than z\n" );  
```  
  
 在此示例中，如果 `x` 小于 `y`，且 `y` 小于 `z`，则调用 `printf` 函数以输出消息。 如果 `x` 大于 `y`，则不会计算第二个操作数 (`y < z`) 且不会输出任何内容。 请注意，如果第二个操作数具有由于某个其他原因而产生的副作用，这可能会导致出现问题。  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 在此示例中，如果 `x` 与 `w`、`y` 或 `z` 相等，则 `printf` 函数的第二个参数的计算结果将为 true，并输出值 1。 否则，它的计算结果将为 false，并打印值 0。 只要其中一个条件的计算结果为 true，计算便会停止。  
  
## <a name="see-also"></a>另请参阅  
 [逻辑“与”运算符：&&](../cpp/logical-and-operator-amp-amp.md)   
 [逻辑“或”运算符：&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)
