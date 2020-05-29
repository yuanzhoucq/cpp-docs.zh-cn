---
title: 按位与或运算符：|
ms.date: 06/14/2018
f1_keywords:
- '|'
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 38def2b1ac585c751699227d2a065b45145d290d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190750"
---
# <a name="bitwise-inclusive-or-operator-"></a>按位与或运算符：|

## <a name="syntax"></a>语法

> *表达式*2 **|** *表达式*2

## <a name="remarks"></a>备注

按位 "或" 运算符 **&#124;** （）将其第一个操作数的每个位与其第二操作数的相应位进行比较。 如果任一位为 1，则对应结果位设置为 1。 否则，相应的结果位设置为 0。

按位“与或”运算符的两个操作数必须为整型。 [标准转换](standard-conversions.md)中涵盖的常用算术转换将应用于操作数。

## <a name="operator-keyword-for-124"></a>运算符关键字&#124;

**Bitor**运算符是的文本等效项 **&#124;** 。 可以通过两种方式访问程序中的**bitor**运算符： > \<包含头文件，或使用[/za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展）编译器选项进行编译。

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

[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 按位运算符](../c-language/c-bitwise-operators.md)
