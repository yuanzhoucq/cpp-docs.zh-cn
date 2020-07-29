---
title: 按位与或运算符： &#124;
description: C + + 标准语言按位或运算符语法，并使用。
ms.date: 07/23/2020
f1_keywords:
- '|'
- bitor_cpp
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 76f80c2101b3acfac71dc4d8ad1be4a999f69aa5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229085"
---
# <a name="bitwise-inclusive-or-operator-124"></a>按位与或运算符： &#124;

## <a name="syntax"></a>语法

> *expression1* **`|`** *expression2*

## <a name="remarks"></a>备注

按位 "或" 运算符（ **`|`** ）将其第一个操作数的每个位与其第二操作数的相应位进行比较。 如果其中一个位是 1，则将对应的结果位设置为 1。 否则，将对应的结果位设置为 0。

运算符的两个操作数必须具有整数类型。 [标准转换](standard-conversions.md)中涵盖的常用算术转换将应用于操作数。

## <a name="operator-keyword-for-124"></a>&#124; 的运算符关键字

C + + **`bitor`** 将指定为的替换拼写 **`|`** 。 在 C 中，可选拼写作为宏在标头中提供 \<iso646.h> 。 在 c + + 中，替换拼写是关键字;\<iso646.h>不推荐使用或 c + + 等效项 \<ciso646> 。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或编译器选项来启用备用拼写。

## <a name="example"></a>示例

```cpp
// expre_Bitwise_Inclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise inclusive OR
#include <iostream>
using namespace std;

int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...
}
```

## <a name="see-also"></a>另请参阅

[C + + 内置运算符、优先级和结合性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 按位运算符](../c-language/c-bitwise-operators.md)
