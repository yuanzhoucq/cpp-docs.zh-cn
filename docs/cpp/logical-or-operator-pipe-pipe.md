---
title: 逻辑 OR 运算符：  &#124;&#124;
description: C + + 标准语言逻辑或运算符语法，并使用。
ms.date: 07/23/2020
f1_keywords:
- '||'
- or_cpp
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 1845aef59f88d5dd044cefedd21cb618e1102e13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225990"
---
# <a name="logical-or-operator-124124"></a>逻辑 OR 运算符：  &#124;&#124;

## <a name="syntax"></a>语法

> *逻辑或表达式* **`||`***逻辑与表达式*

## <a name="remarks"></a>备注

**`||`** **`true`** 如果有一个或两个操作数为，则逻辑 OR 运算符（）返回布尔值 **`true`** ， **`false`** 否则返回。 操作数在计算前隐式转换为类型 **`bool`** ，结果为类型 **`bool`** 。 逻辑“或”具有从左向右的关联性。

逻辑 OR 运算符的操作数不必具有相同的类型，但它们必须为布尔值、整型值或指针类型。 操作数通常为关系或相等表达式。

第一个操作数将完全计算，并且在继续计算逻辑“或”表达式之前将完成所有副作用。

仅当第一个操作数的计算结果为时才计算第二个操作数 **`false`** ，因为逻辑 OR 表达式为时，不需要进行计算 **`true`** 。 这称为 "*短路*计算"。

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

在上面的示例中，如果 `x` 等于 `w` 、 `y` 或 `z` ，则函数的第二个参数的 `printf` 计算结果为 **`true`** ，然后将其提升为整数，并打印值1。 否则，计算结果为 **`false`** ，并打印值0。 当某个条件的计算结果为时 **`true`** ，将停止计算。

## <a name="operator-keyword-for-124124"></a> &#124;&#124; 的运算符关键字

C + + **`or`** 将指定为的替换拼写 **`||`** 。 在 C 中，可选拼写作为宏在标头中提供 \<iso646.h> 。 在 c + + 中，替换拼写是关键字;\<iso646.h>不推荐使用或 c + + 等效项 \<ciso646> 。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或编译器选项来启用备用拼写。

## <a name="example"></a>示例

```cpp
// expre_Logical_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate logical OR
#include <iostream>
using namespace std;
int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b || b > c yields "
         << (a < b || b > c) << endl
         << "The false expression "
         << "a > b || b > c yields "
         << (a > b || b > c) << endl;
}
```

## <a name="see-also"></a>另请参阅

[C + + 内置运算符、优先级和结合性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 逻辑运算符](../c-language/c-logical-operators.md)
