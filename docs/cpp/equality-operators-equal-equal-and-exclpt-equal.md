---
title: 相等运算符：== 和 !=
description: C + + 标准语言等于和不等于运算符语法，并使用。
ms.date: 07/23/2020
f1_keywords:
- '!='
- ==
- not_eq_cpp
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: 567b83e99dce0354626f08a4788f1343314493b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227538"
---
# <a name="equality-operators--and-"></a>相等运算符：== 和 !=

## <a name="syntax"></a>语法

> *表达式* **`==`***表达式*\
> *表达式* **`!=`***表达式*

## <a name="remarks"></a>备注

二元相等运算符将严格比较其操作数的相等性或不相等性。

等于（ **`==`** ）和不等于（）的相等运算符的 **`!=`** 优先级低于关系运算符，但其行为方式类似。 这些运算符的结果类型是 **`bool`** 。

**`==`** **`true`** 如果两个操作数具有相同的值，则返回等于运算符（）; 否则返回 **`false`** 。 **`!=`** 如果操作数的值不相同，则不等于运算符（）返回 **`true`** ; 否则返回 **`false`** 。

## <a name="operator-keyword-for-"></a>！ = 的运算符关键字

C + + **`not_eq`** 将指定为的替换拼写 **`!=`** 。 （不存在对的其他拼写检查 **`==`** 。）在 C 中，可选拼写作为宏在标头中提供 \<iso646.h> 。 在 c + + 中，替换拼写是关键字;\<iso646.h>不推荐使用或 c + + 等效项 \<ciso646> 。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或编译器选项来启用备用拼写。

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
[C + + 内置运算符，优先级;和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 关系和相等运算符](../c-language/c-relational-and-equality-operators.md)
