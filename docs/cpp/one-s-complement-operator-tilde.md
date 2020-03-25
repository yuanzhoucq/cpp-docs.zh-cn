---
title: 一个&#39;补码运算符： ~
ms.date: 11/04/2016
f1_keywords:
- "~"
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: 777f253925caf38647863bdaa93fde8d5a03e3f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177711"
---
# <a name="one39s-complement-operator-"></a>一个&#39;补码运算符： ~

## <a name="syntax"></a>语法

```
~ cast-expression
```

## <a name="remarks"></a>备注

二进制反码运算符 (`~`)（有时称为“按位反码”运算符）将生成其操作数的按位二进制反码。 即，操作数中为 1 的每个位在结果中为 0。 相反，操作数中为 0 的每个位在结果中为 1。 二进制反码运算符的操作数必须为整型。

## <a name="operator-keyword-for-"></a>~ 的运算符关键字

**Compl**运算符是 `~`的文本等效项。 可以通过两种方式访问程序中的**compl**运算符：包含头文件 `iso646.h`或使用[/za](../build/reference/za-ze-disable-language-extensions.md)进行编译。

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

将对整型操作数执行整型提升，并且结果类型将是操作数将提升到的类型。 有关如何完成升级的详细信息，请参阅[标准转换](standard-conversions.md)。

## <a name="see-also"></a>另请参阅

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[一元算术运算符](../c-language/unary-arithmetic-operators.md)
