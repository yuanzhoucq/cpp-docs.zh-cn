---
title: 结构和联合成员 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators
- structure members, referencing
- -> operator, structure and union members
- dot operator (.)
- referencing structure members
- . operator
- operators [C], member selection
- structure member selection
ms.assetid: bb1fe304-af49-4f98-808d-afdc99b3e319
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cf98987323b96c8b3977e9a6d2bc590e0b612b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="structure-and-union-members"></a>结构和联合成员
“成员选择表达式”是指结构和联合的成员。 此类表达式具有选定成员的值和类型。  
  
```  
  
postfix-expression  
.  
identifier  
postfix-expression  
->  
identifier  
  
```  
  
 此列表描述了成员选择表达式的两种形式：  
  
1.  在第一种形式中，*postfix-expression* 表示 `struct` 或 **union** 类型的值，而 *identifier* 为指定的结构或联合的成员命名。 运算的值是 *identifier* 的值且是一个左值（如果 *postfix-expression* 是左值）。 有关详细信息，请参阅[左值和右值表达式](../c-language/l-value-and-r-value-expressions.md)。  
  
2.  在第二种形式中，*postfix-expression* 表示指向结构或联合的指针，而 *identifier* 命名指定的结构或联合的成员。 该值是 *identifier* 的值且是一个左值。  
  
 成员选择表达式的两种形式具有类似的效果。  
  
 实际上，如果句点前面的表达式由适用于指针值的间接寻址运算符 (**\***) 构成，则包含成员选择运算符 (**->**) 的表达式是使用句点 (**.**) 的表达式的速记版。 因此，  
  
```  
  
expression  
->  
identifier  
  
```  
  
 等效于  
  
```  
  
(*  
expression  
) .  
identifier  
  
```  
  
 当 *expression* 为指针值时。  
  
## <a name="examples"></a>示例  
 以下示例引用此结构声明。 有关这些示例中使用的间接寻址运算符 (**\***) 的信息，请参阅[间接寻址运算符和 Address-of 运算符](../c-language/indirection-and-address-of-operators.md)。  
  
```  
struct pair   
{  
    int a;  
    int b;  
    struct pair *sp;  
} item, list[10];  
```  
  
 `item` 结构的成员选择表达式与下面类似：  
  
```  
item.sp = &item;  
```  
  
 在上面的示例中，将 `item` 结构的地址分配给结构的 `sp` 成员。 这意味着，`item` 包含一个指向自身的指针。  
  
```  
(item.sp)->a = 24;  
```  
  
 在此示例中，将指针表达式 `item.sp` 与成员选择运算符 (**->**) 一起使用以便将值赋给成员 `a`。  
  
```  
list[8].b = 12;  
```  
  
 此语句演示如何从结构数组中选择单个结构成员。  
  
## <a name="see-also"></a>请参阅  
 [成员访问运算符：. 和 ->](../cpp/member-access-operators-dot-and.md)