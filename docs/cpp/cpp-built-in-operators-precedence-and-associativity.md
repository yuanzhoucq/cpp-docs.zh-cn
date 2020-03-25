---
title: C++ 内置运算符、 优先级和关联性
ms.date: 11/04/2016
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
ms.openlocfilehash: 36e7ce77e24366be10b75f5bb4f8830363594301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180402"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C++ 内置运算符、 优先级和关联性

C++ 语言包括所有 C 运算符并添加多个新的运算符。 运算符指定对一个或多个操作数执行的计算。

运算符*优先级*指定包含多个运算符的表达式中的运算顺序。 运算符*关联*性指定是否在包含多个具有相同优先级的运算符的表达式中，将操作数分组在其左侧或右侧的一个。 下表显示 C++ 运算符的优先级和关联性（从最高优先级到最低优先级）。 优先级别编号相同的运算符具有等同的优先级别，除非由括号显式施加另一种关系。

### <a name="c-operator-precedence-and-associativity"></a>C++ 运算符的优先级和关联性

|运算符说明|Operator|
|--------------------------|--------------|
|**组1优先级，无关联性**|
|[作用域解析](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**组2优先顺序，从左到右的关联性**|
|[成员选择（对象或指针）](../cpp/member-access-operators-dot-and.md)|[.或->](../cpp/member-access-operators-dot-and.md)|
|[数组下标](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[函数调用](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[后缀递增](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[后缀减量](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[类型名称](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[常量类型转换](../cpp/const-cast-operator.md)|[const_cast](../cpp/const-cast-operator.md)|
|[动态类型转换](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[重新解释类型转换](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[静态类型转换](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**组3优先级，从右到左关联性**|
|[对象或类型的大小](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[前缀递增](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[前缀减量](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[1的补码](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[逻辑非](../cpp/logical-negation-operator-exclpt.md)|[\!](../cpp/logical-negation-operator-exclpt.md)|
|[一元求反](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[一元加](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Address-of](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[二级](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[创建对象](../cpp/new-operator-cpp.md)|[new](../cpp/new-operator-cpp.md)|
|[销毁对象](../cpp/delete-operator-cpp.md)|[delete](../cpp/delete-operator-cpp.md)|
|[强制转换](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**组4优先级，从左到右的关联性**|
|[指向成员的指针（对象或指针）](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[.&#42;或->&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**组5优先级，从左到右的关联性**|
|[乘法](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[除法](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[模块](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**组6优先顺序，从左到右的关联性**|
|[加法](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[减法](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**组7优先级，从左到右的关联性**|
|[左移](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[右移](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**组8优先级，从左到右的关联性**|
|[小于](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[大于](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[小于或等于](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[大于或等于](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**组9优先级，从左到右的关联性**|
|[相等](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[不相等](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[\!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**组10优先级从左到右的关联性**|
|[按位“与”](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**组11优先级，从左到右的关联性**|
|[位异或](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**组12优先级，从左到右的关联性**|
|[按位 "或"](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**组13优先级，从左到右的关联性**|
|[逻辑“与”](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**组14优先级，从左到右的关联性**|
|[逻辑“或”](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**分组15优先级，从右到左关联性**|
|[增值税](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**组16优先级，从右到左关联性**|
|[赋值](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[乘法赋值](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[除法赋值](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[取模赋值](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[加法赋值](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[减法赋值](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[左移赋值](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[右移赋值](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[按位 AND 赋值](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[按位 "或" 赋值](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[按位异或赋值](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**组17优先级，从右到左的关联性**|
|[throw 表达式](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**组18优先级，从左到右的关联性**|
|[逗号](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>请参阅

[运算符重载](operator-overloading.md)
