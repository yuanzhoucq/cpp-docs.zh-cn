---
title: 相等运算符：== 和 !=
ms.date: 11/04/2016
f1_keywords:
- '!='
- ==
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: 7e42b66438579bc9be6274863366762b8b4ffbe9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444397"
---
# <a name="equality-operators--and-"></a>相等运算符：== 和 !=

## <a name="syntax"></a>语法

```
expression == expression
expression != expression
```

## <a name="remarks"></a>备注

二元相等运算符将严格比较其操作数的相等性或不相等性。

相等运算符（等于 (`==`) 而不等于 (`!=`)）的优先级低于关系运算符的优先级，但其行为类似。 这些运算符的结果类型为**bool**。

如果两个操作数具有相同的值，则等于运算符（`==`）返回**true** （1）;否则，它将返回**false** （0）。 如果操作数不具有相同的值，则不等于运算符（`!=`）返回**true** ;否则，返回**false**。

## <a name="operator-keyword-for-"></a>!= 的运算符关键字

`not_eq` 运算符是 `!=` 的文本等效项。 可以通过两种方式在程序中访问 `not_eq` 运算符： `iso646.h`中包含头文件，或使用[/za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展）编译器选项进行编译。

## <a name="example"></a>示例

```cpp
// expre_Equality_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << boolalpha
         << "The true expression 3 != 2 yields: "
         << (3 != 2) << endl
         << "The false expression 20 == 10 yields: "
         << (20 == 10) << endl;
}
```

相等运算符可比较指向同一类型的成员的指针。 在这种比较中，将执行指向成员的指针转换。 指向成员的指针也可以与计算结果为 0 的常量表达式进行比较。

## <a name="see-also"></a>另请参阅

[使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 关系和相等运算符](../c-language/c-relational-and-equality-operators.md)