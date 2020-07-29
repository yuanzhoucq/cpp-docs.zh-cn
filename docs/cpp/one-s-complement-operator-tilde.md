---
title: 二进制求补运算符：~
description: C + + 标准语言的补码运算符语法和用法。
ms.date: 07/23/2020
f1_keywords:
- "~"
- compl_cpp
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: 89c67855cd67df2af315cea941b487e7462889b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227239"
---
# <a name="ones-complement-operator-"></a>二进制求补运算符：~

## <a name="syntax"></a>语法

```cpp
~ cast-expression
```

## <a name="remarks"></a>备注

1的补数运算符（ **`~`** ），有时称为*按位求补*运算符，产生其操作数的按位二进制反码。 即，操作数中为 1 的每个位在结果中为 0。 相反，操作数中为 0 的每个位在结果中为 1。 二进制反码运算符的操作数必须为整型。

## <a name="operator-keyword-for-"></a>~ 的运算符关键字

C + + **`compl`** 将指定为的替换拼写 **`~`** 。 在 C 中，可选拼写作为宏在标头中提供 \<iso646.h> 。 在 c + + 中，替换拼写是关键字;\<iso646.h>不推荐使用或 c + + 等效项 \<ciso646> 。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或编译器选项来启用备用拼写。

## <a name="example"></a>示例

```cpp
// expre_One_Complement_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main () {
   unsigned short y = 0xFFFF;
   cout << hex << y << endl;
   y = ~y;   // Take one's complement
   cout << hex << y << endl;
}
```

在此示例中，分配给 `y` 的新值是无符号值 0xFFFF 或 0x0000 的二进制反码。

整型提升是对整型操作数执行的。 操作数升级为的类型为结果类型。 有关整数提升的详细信息，请参阅[标准转换](standard-conversions.md)。

## <a name="see-also"></a>另请参阅

[带有一元运算符的表达式](expressions-with-unary-operators.md)<br/>
[C + + 内置运算符、优先级和结合性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[一元算术运算符](../c-language/unary-arithmetic-operators.md)
