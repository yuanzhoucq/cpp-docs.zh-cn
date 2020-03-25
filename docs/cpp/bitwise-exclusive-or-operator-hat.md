---
title: 按位异或运算符：^
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 9a44dc60a985729aae79ed0e2e48c44adace647b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190711"
---
# <a name="bitwise-exclusive-or-operator-"></a>按位异或运算符：^

## <a name="syntax"></a>语法

```
expression ^ expression
```

## <a name="remarks"></a>备注

按位 "异或" 运算符（ **^** ）将第一个操作数的每个位与其第二操作数的相应位进行比较。 如果一位是 0，另一对应位是 1，则相应结果位设置为 1。 否则，相应的结果位设置为 0。

按位“异或”运算符的两个操作数都必须为整型。 [标准转换](standard-conversions.md)中涵盖的常用算术转换将应用于操作数。

## <a name="operator-keyword-for-"></a>^ 的运算符关键字

**Xor**运算符是 **^** 的文本等效项。 可以通过两种方式访问程序中的**xor**运算符：包含头文件 `iso646.h`或使用[/za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展）编译器选项编译。

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

[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
