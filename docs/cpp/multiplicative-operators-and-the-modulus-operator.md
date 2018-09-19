---
title: 乘法运算符和取模运算符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '%'
- /
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator [C++]
- '* operator'
- division operator [C++], multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02d6d7d5d8f6c7dcce54e1dff54795b253d9d04a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106043"
---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>乘法运算符和取模运算符

## <a name="syntax"></a>语法

```
expression * expression 
expression / expression 
expression % expression
```

## <a name="remarks"></a>备注

乘法运算符为：

- 乘法 (<strong>\*</strong>)

- 除法 (**/**)

- 取模 （除法运算的余数） (**%**)

这些二进制运算符具有从左至右的关联性。

乘法运算符采用算术类型的操作数。 取模运算符 (**%**) 具有更严格的要求，即其操作数必须是整型。 (若要获取浮点除法的余数，请使用运行时函数[fmod](../c-runtime-library/reference/fmod-fmodf.md)。)中涵盖的转换[标准转换](standard-conversions.md)适用于操作数，结果为转换的类型。

除法运算符产生的结果为将第一个操作数乘以第二个操作数所获得的结果。

除法运算符产生的结果为将第一个操作数除以第二个操作数所获得的结果。

取模运算符产生下列表达式给定的余数， *e1*是第一个操作数和*e2*是第二部分： *e1* -(*e1* /  *e2*) \* *e2*、 两个操作数均为整型。

在除法或取模表达式中被 0 除的结果是不确定的，将会导致运行时错误。 因此，以下表达式生成未定义的错误结果：

```cpp
i % 0
f / 0.0
```

如果乘法、除法或取模表达式的两个操作数具有相同的符号，则结果为正。 否则，结果为负。 取模运算的符号的结果是实现定义的。

> [!NOTE]
>  由于在溢出或下溢条件不提供由乘法运算符执行的转换，因此，如果乘法操作的结果在转换后不能用操作数类型表示，则信息可能丢失。

**Microsoft 专用**

在 Microsoft C++ 中，取模表达式的结果的符号始终与第一个操作数的符号相同。

**结束 Microsoft 专用**

如果两个整数的减法计算不准确，并且只有一个操作数为负，则结果是最大的整数（在数量级上，忽略符号），该整数小于减法运算所生成的准确值。 例如，-11 的计算的值除以 3 得-3.666666666。 该整数除法运算的结果为-3。

乘法运算符之间的关系提供由标识 (*e1* / *e2*) \* *e2*  +  *e1* % *e2* == *e1*。

## <a name="example"></a>示例

以下程序演示乘法运算符。 请注意的其中一个操作数`10 / 3`必须显式强制转换为类型**float**若要避免截断，以便这两个操作数均为类型**float**除法运算前。

```cpp
// expre_Multiplicative_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   int x = 3, y = 6, z = 10;
   cout  << "3 * 6 is " << x * y << endl
         << "6 / 3 is " << y / x << endl
         << "10 % 3 is " << z % x << endl
         << "10 / 3 is " << (float) z / x << endl;
}
```

## <a name="see-also"></a>请参阅

[使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 乘法运算符](../c-language/c-multiplicative-operators.md)