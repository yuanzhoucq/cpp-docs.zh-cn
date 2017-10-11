---
title: "C + + 内置运算符、 优先级和结合性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators (C++), hierarchy
- operator precedence
- precedence, operators
- operators (C++), associativity
- multiple operators [C++]
- associativity of operators [C++]
- operators [C++], precedence
- evaluation order
- hierarchy, operator
ms.assetid: 95c1f0ba-dad8-4034-b039-f79a904f112f
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6c45b0d3ff2aaee6763b73949727dcde5ee744bc
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C + + 内置运算符、 优先级和关联性
C++ 语言包括所有 C 运算符并添加多个新的运算符。 运算符指定对一个或多个操作数执行的计算。  
  
 运算符优先级别指定包含多个运算符的表达式中的运算顺序。 运算符关联性指定，在包含多个具有相同优先级别的运算符的表达式中，操作数与其左侧还是右侧的操作数组合。 下表显示 C++ 运算符的优先级和关联性（从最高优先级到最低优先级）。 优先级别编号相同的运算符具有等同的优先级别，除非由括号显式施加另一种关系。  
  
### <a name="c-operator-precedence-and-associativity"></a>C++ 运算符的优先级和关联性  
  
|运算符说明|运算符|  
|--------------------------|--------------|  
|`Group 1 precedence, no associativity`|  
|[范围解析](../cpp/scope-resolution-operator.md)|`::`|  
|`Group 2 precedence, left to right associativity`|  
|[成员选择 （对象或指针）](../cpp/member-access-operators-dot-and.md)|`. or ->`|  
|[数组下标](../cpp/subscript-operator.md)|`[ ]`|  
|[函数调用](../cpp/function-call-operator-parens.md)|`( )`|  
|[后缀递增](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|`++`|  
|[后缀递减](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|`--`|  
|[类型名称](../cpp/typeid-operator.md)|`typeid( )`|  
|[常量类型转换](../cpp/const-cast-operator.md)|`const_cast`|  
|[动态类型转换](../cpp/dynamic-cast-operator.md)|`dynamic_cast`|  
|[重新解释后的类型转换](../cpp/reinterpret-cast-operator.md)|`reinterpret_cast`|  
|[静态类型转换](../cpp/static-cast-operator.md)|`static_cast`|  
|`Group 3 precedence, right to left associativity`|  
|[对象或类型的大小](../cpp/sizeof-operator.md)|`sizeof`|  
|[前缀递增](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|`++`|  
|[前缀递减](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|`--`|  
|[二进制反码](../cpp/one-s-complement-operator-tilde.md)|`~`|  
|[逻辑非](../cpp/logical-negation-operator-exclpt.md)|`!`|  
|[一元求反](../cpp/unary-plus-and-negation-operators-plus-and.md)|`-`|  
|[一元加](../cpp/unary-plus-and-negation-operators-plus-and.md)|`+`|  
|[地址的](../cpp/lvalue-reference-declarator-amp.md)|`&`|  
|[间接寻址](../cpp/indirection-operator-star.md)|`*`|  
|[创建对象](../cpp/new-operator-cpp.md)|`new`|  
|[销毁对象](../cpp/delete-operator-cpp.md)|`delete`|  
|[强制转换](../cpp/cast-operator-parens.md)|`Cast: ()`|  
|`Group 4 precedence, left to right associativity`|  
|[指针到成员 （对象或指针）](../cpp/pointer-to-member-operators-dot-star-and-star.md)|`.* or ->*`|  
|`Group 5 precedence, left to right associativity`|  
|[乘法](../cpp/multiplicative-operators-and-the-modulus-operator.md)|`*`|  
|[除法](../cpp/multiplicative-operators-and-the-modulus-operator.md)|`/`|  
|[取模](../cpp/multiplicative-operators-and-the-modulus-operator.md)|`%`|  
|`Group 6 precedence, left to right associativity`|  
|[添加](../cpp/additive-operators-plus-and.md)|`+`|  
|[减法](../cpp/additive-operators-plus-and.md)|`-`|  
|`Group 7 precedence, left to right associativity`|  
|[左的移](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|`<<`|  
|[右移位](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|`>>`|  
|`Group 8 precedence, left to right associativity`|  
|[小于](../cpp/relational-operators-equal-and-equal.md)|`<`|  
|[大于](../cpp/relational-operators-equal-and-equal.md)|`>`|  
|[小于或等于](../cpp/relational-operators-equal-and-equal.md)|`<=`|  
|[大于或等于](../cpp/relational-operators-equal-and-equal.md)|`>=`|  
|`Group 9 precedence, left to right associativity`|  
|[相等性](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|`==`|  
|[不相等](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|`!=`|  
|`Group 10 precedence left to right associativity`|  
|[按位与](../cpp/bitwise-and-operator-amp.md)|`&`|  
|`Group 11 precedence, left to right associativity`|  
|[按位异或](../cpp/bitwise-exclusive-or-operator-hat.md)|`^`|  
|`Group 12 precedence, left to right associativity`|  
|[按位与或](../cpp/bitwise-inclusive-or-operator-pipe.md)|`&#124;`|  
|`Group 13 precedence, left to right associativity`|  
|[逻辑与](../cpp/logical-and-operator-amp-amp.md)|`&&`|  
|`Group 14 precedence, left to right associativity`|  
|[逻辑或](../cpp/logical-or-operator-pipe-pipe.md)|`&#124;&#124;`|  
|`Group 15 precedence, right to left associativity`|  
|[条件](../cpp/conditional-operator-q.md)|`? :`|  
|`Group 16 precedence, right to left associativity`|  
|[赋值](../cpp/assignment-operators.md)|`=`|  
|[乘法赋值](../cpp/assignment-operators.md)|`*=`|  
|[除法赋值](../cpp/assignment-operators.md)|`/=`|  
|[取模赋值](../cpp/assignment-operators.md)|`%=`|  
|[加法赋值](../cpp/assignment-operators.md)|`+=`|  
|[减法赋值](../cpp/assignment-operators.md)|`-=`|  
|[左移赋值](../cpp/assignment-operators.md)|`<<=`|  
|[右移赋值](../cpp/assignment-operators.md)|`>>=`|  
|[按位与赋值](../cpp/assignment-operators.md)|`&=`|  
|[按位与或赋值](../cpp/assignment-operators.md)|`&#124;=`|  
|[按位异或赋值](../cpp/assignment-operators.md)|`^=`|  
|`Group 17 precedence, right to left associativity`|  
|[引发表达式](../cpp/try-throw-and-catch-statements-cpp.md)|`throw`|  
|`Group 18 precedence, left to right associativity`|  
|[逗号](../cpp/comma-operator.md)|`,`|  
  
## <a name="see-also"></a>另请参阅  
[运算符重载](operator-overloading.md)



