---
title: 乘法运算符和取模运算符
ms.date: 11/04/2016
f1_keywords:
- '%'
- /
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
ms.openlocfilehash: c277c93640201de69a4cb29060bc5191aa91629c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227356"
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

- 乘法（ <strong>\*</strong> ）

- 除号（ **/** ）

- 取模（余数除以除法）（ **%** ）

这些二进制运算符具有从左至右的关联性。

乘法运算符采用算术类型的操作数。 取模运算符（ **%** ）具有更严格的要求，因为其操作数必须是整型。 （若要获取浮点除法的余数，请使用运行时函数[fmod](../c-runtime-library/reference/fmod-fmodf.md)。）[标准转换](standard-conversions.md)中涵盖的转换适用于操作数，并且结果为转换后的类型。

除法运算符产生的结果为将第一个操作数乘以第二个操作数所获得的结果。

除法运算符产生的结果为将第一个操作数除以第二个操作数所获得的结果。

取模运算符会产生下面的表达式所指定的余数，其中， *e1*是第一个操作数， *e2*为第二个操作数： *e1* -（*e1*  /  *e2*） \* *e2*，其中两个操作数均为整型类型。

在除法或取模表达式中被 0 除的结果是不确定的，将会导致运行时错误。 因此，以下表达式生成未定义的错误结果：

```cpp
i % 0
f / 0.0
```

如果乘法、除法或取模表达式的两个操作数具有相同的符号，则结果为正。 否则，结果为负。 取模运算的符号的结果是实现定义的。

> [!NOTE]
> 由于在溢出或下溢条件不提供由乘法运算符执行的转换，因此，如果乘法操作的结果在转换后不能用操作数类型表示，则信息可能丢失。

**Microsoft 专用**

在 Microsoft C++ 中，取模表达式的结果的符号始终与第一个操作数的符号相同。

**结束 Microsoft 专用**

如果两个整数的减法计算不准确，并且只有一个操作数为负，则结果是最大的整数（在数量级上，忽略符号），该整数小于减法运算所生成的准确值。 例如，-11/3 的计算值为-3.666666666。 整数相除的结果为-3。

乘法运算符之间的关系由标识（*e1*  /  *e2*） \* *e2*  +  *e1*  %  *e2*  ==  *e1*提供。

## <a name="example"></a>示例

以下程序演示乘法运算符。 请注意，必须将的任一操作数 `10 / 3` 显式转换为类型 **`float`** 以避免截断，以便两个操作数的类型为 " **`float`** 相除"。

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

## <a name="see-also"></a>另请参阅

[带有二元运算符的表达式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 乘法运算符](../c-language/c-multiplicative-operators.md)
