---
title: 逻辑非运算符：!
ms.date: 08/27/2018
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: 06142ef15fcdbafdbae4b892772a04b117c087f6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446535"
---
# <a name="logical-negation-operator-"></a>逻辑非运算符：!

## <a name="syntax"></a>语法

```
! cast-expression
```

## <a name="remarks"></a>备注

逻辑求反运算符（ **！** ）反转操作数的含义。 操作数必须是算法或指针类型（或计算结果为算法或指针类型的表达式）。 操作数隐式转换为**bool**类型。 如果转换后的操作数为 FALSE，则结果为 TRUE;如果转换后的操作数为 TRUE，则结果为 FALSE。 结果的类型为**bool**。

对于表达式*e*，一元表达式 `!e` 等效于表达式 `(e == 0)`（涉及重载运算符的情况除外）。

## <a name="operator-keyword-for-"></a>! 的运算符关键字

**Not**运算符是 **！** 的替代拼写。 可以通过两种方式在程序中访问**not**运算符：包含头文件 \<iso646 >，或使用[/za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展）编译器选项进行编译。

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

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[一元算术运算符](../c-language/unary-arithmetic-operators.md)<br/>
