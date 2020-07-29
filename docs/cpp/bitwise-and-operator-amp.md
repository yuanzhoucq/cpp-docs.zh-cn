---
title: 位与运算符：&amp;
description: C + + 标准语言按位与运算符语法，并使用。
ms.date: 07/23/2020
f1_keywords:
- bitand_cpp
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: 7e78e4003a31ee59ebd974275df784b7a76e73ce
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229111"
---
# <a name="bitwise-and-operator-amp"></a>位与运算符：&amp;

## <a name="syntax"></a>语法

> *表达式* **`&`***表达式*

## <a name="remarks"></a>备注

按位 "与" 运算符（ **`&`** ）将第一个操作数的每个位与第二操作数的相应位进行比较。 如果两个位均为 1，则对应的结果位将设置为 1。 否则，将对应的结果位设置为 0。

按位 "与" 运算符的两个操作数都必须是整数类型。 [标准转换](standard-conversions.md)中涵盖的常用算术转换将应用于操作数。

## <a name="operator-keyword-for-"></a>& 的运算符关键字

C + + **`bitand`** 将指定为的替换拼写 **`&`** 。 在 C 中，可选拼写作为宏在标头中提供 \<iso646.h> 。 在 c + + 中，替换拼写是关键字;\<iso646.h>不推荐使用或 c + + 等效项 \<ciso646> 。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或编译器选项来启用备用拼写。

## <a name="example"></a>示例

```cpp
// expre_Bitwise_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise AND
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0xFFFF;      // pattern 1111 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...
}
```

## <a name="see-also"></a>另请参阅

[C + + 内置运算符、优先级和结合性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 按位运算符](../c-language/c-bitwise-operators.md)
