---
title: 逻辑非运算符：!
description: C + + 标准语言逻辑求反运算符语法和用法。
ms.date: 07/23/2020
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: fdd2e7a71b791375f898372d058a5eeb2afc59f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223676"
---
# <a name="logical-negation-operator-"></a>逻辑非运算符：!

## <a name="syntax"></a>语法

> **`!`***cast 表达式*

## <a name="remarks"></a>备注

逻辑求反运算符（ **`!`** ）反转操作数的含义。 操作数必须是算法或指针类型（或计算结果为算法或指针类型的表达式）。 操作数将隐式转换为类型 **`bool`** 。 如果转换后的操作数为，则结果为 **`true`** **`false`** ; **`false`** 如果转换的操作数为，则结果为 **`true`** 。 结果的类型为 **`bool`** 。

对于表达式 `e` ，一元表达式 `!e` 等效于表达式 `(e == 0)` （涉及重载运算符的情况除外）。

## <a name="operator-keyword-for-"></a>运算符关键字适用于！

C + + **`not`** 将指定为的替换拼写 **`!`** 。 在 C 中，可选拼写作为宏在标头中提供 \<iso646.h> 。 在 c + + 中，替换拼写是关键字;\<iso646.h>不推荐使用或 c + + 等效项 \<ciso646> 。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或编译器选项来启用备用拼写。

## <a name="example"></a>示例

```cpp
// expre_Logical_NOT_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    if (!i)
        cout << "i is zero" << endl;
}
```

## <a name="see-also"></a>另请参阅

[带有一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[C + + 内置运算符、优先级和结合性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[一元算术运算符](../c-language/unary-arithmetic-operators.md)<br/>
