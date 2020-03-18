---
title: 按位与运算符： &amp;
ms.date: 11/04/2016
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: ba17c9a633b7b18cad2881dfef90fde7c2074319
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446141"
---
# <a name="bitwise-and-operator-amp"></a>按位与运算符： &amp;

## <a name="syntax"></a>语法

```
expression & expression
```

## <a name="remarks"></a>备注

表达式可以是其他“与”表达式，或（遵循下面所述的类型限制）相等表达式、关系表达式、加法表达式、乘法表达式、指向成员的指针表达式、强制转换表达式、一元表达式、后缀表达式或主表达式。

按位 "与" 运算符（ **&** ）将第一个操作数的每个位与第二操作数的相应位进行比较。 如果两个位均为 1，则对应的结果位将设置为 1。 否则，将对应的结果位设置为 0。

按位“与”运算符的两个操作数必须为整型。 [标准转换](standard-conversions.md)中涵盖的常用算术转换将应用于操作数。

## <a name="operator-keyword-for-"></a>& 的运算符关键字

**Bitand**运算符是 **&** 的文本等效项。 可以通过两种方式在程序中访问**bitand**运算符： `iso646.h`中包含头文件，或使用[/za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展）编译器选项进行编译。

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

[C++ 内置运算符、优先级和关联性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 按位运算符](../c-language/c-bitwise-operators.md)