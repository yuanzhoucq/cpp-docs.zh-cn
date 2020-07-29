---
title: 按位异或运算符：^
description: C + + 标准语言专用或运算符语法，并使用。
ms.date: 07/23/2020
f1_keywords:
- xor_cpp
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 0f64b9f90b70756d29fcabb361cc07abe58e0a54
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229098"
---
# <a name="bitwise-exclusive-or-operator-"></a>按位异或运算符：^

## <a name="syntax"></a>语法

> *表达式* **`^`***表达式*

## <a name="remarks"></a>备注

按位 "异或" 运算符（ **`^`** ）将第一个操作数的每个位与其第二操作数的相应位进行比较。 如果第一个操作数中的位是0，另一个位是1，则相应的结果位将设置为1。 否则，将对应的结果位设置为 0。

运算符的两个操作数必须具有整数类型。 [标准转换](standard-conversions.md)中涵盖的常用算术转换将应用于操作数。

## <a name="operator-keyword-for-"></a>^ 运算符关键字

C + + **`xor`** 将指定为的替换拼写 **`^`** 。 在 C 中，可选拼写作为宏在标头中提供 \<iso646.h> 。 在 c + + 中，替换拼写是关键字;\<iso646.h>不推荐使用或 c + + 等效项 \<ciso646> 。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或编译器选项来启用备用拼写。


## <a name="example"></a>示例

```cpp
// expre_Bitwise_Exclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise exclusive OR
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xFFFF;      // pattern 1111 ...

   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...
}
```

## <a name="see-also"></a>另请参阅

[C + + 内置运算符、优先级和结合性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
