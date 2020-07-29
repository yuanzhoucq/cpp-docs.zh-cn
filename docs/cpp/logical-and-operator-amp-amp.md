---
title: 逻辑 AND 运算符：&amp;&amp;
description: C + + 标准语言逻辑 AND 运算符语法和用法。
ms.date: 07/23/2020
f1_keywords:
- '&&'
- and_cpp
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
ms.openlocfilehash: 431e76a2943c2373d6191f1fbe9f14c54cfaa6c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223689"
---
# <a name="logical-and-operator-ampamp"></a>逻辑 AND 运算符：&amp;&amp;

## <a name="syntax"></a>语法

> *表达式* **`&&`***表达式*

## <a name="remarks"></a>备注

**&&** **`true`** 如果两个操作数都为，则逻辑 "与" 运算符（）返回 **`true`** ， **`false`** 否则返回。 操作数在计算前隐式转换为类型 **`bool`** ，结果为类型 **`bool`** 。 逻辑“与”具有从左到右的关联性。

逻辑 AND 运算符的操作数不需要具有相同的类型，但它们必须具有 boolean、整型或指针类型。 操作数通常为关系或相等表达式。

完全计算第一个操作数，并在对逻辑 AND 表达式的计算继续之前完成所有副作用。

仅当第一个操作数的计算结果为 **`true`** （非零）时，才计算第二个操作数。 如果逻辑 AND 表达式为，则此计算将消除第二个操作数的不必要计算 **`false`** 。 可以使用此短路计算防止 null 指针取消引用，如以下示例所示：

```cpp
char *pch = 0;
// ...
(pch) && (*pch = 'a');
```

如果 `pch` 为 null (0)，则从不计算表达式的右侧。 此短路计算使赋值无法通过空指针实现。

## <a name="operator-keyword-for-"></a> && 的运算符关键字

C + + **`and`** 将指定为的替换拼写 **`&&`** 。 在 C 中，可选拼写作为宏在标头中提供 \<iso646.h> 。 在 c + + 中，替换拼写是关键字;\<iso646.h>不推荐使用或 c + + 等效项 \<ciso646> 。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或编译器选项来启用备用拼写。

## <a name="example"></a>示例

```cpp
// expre_Logical_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate logical AND
#include <iostream>

using namespace std;

int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b && b < c yields "
         << (a < b && b < c) << endl
         << "The false expression "
         << "a > b && b < c yields "
         << (a > b && b < c) << endl;
}
```

## <a name="see-also"></a>另请参阅

[C + + 内置运算符、优先级和结合性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 逻辑运算符](../c-language/c-logical-operators.md)
