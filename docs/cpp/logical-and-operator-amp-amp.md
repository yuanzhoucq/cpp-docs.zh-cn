---
title: 逻辑 AND 运算符： &amp;&amp;
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
ms.openlocfilehash: b21d91009c455b67af6fae88fceafeeaf8043301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179427"
---
# <a name="logical-and-operator-ampamp"></a>逻辑 AND 运算符： &amp;&amp;

## <a name="syntax"></a>语法

```
expression && expression
```

## <a name="remarks"></a>备注

如果两个操作数都为 TRUE，则逻辑 "与" 运算符（ **&&** ）返回布尔值 true，否则返回 FALSE。 操作数在计算前隐式转换为**bool**类型，结果为**bool**类型。 逻辑“与”具有从左到右的关联性。

逻辑“与”运算符的操作数不需要具有相同的类型，但它们必须是整数或指针类型。 操作数通常为关系或相等表达式。

第一个操作数将完全计算，在继续对逻辑“与”表达式进行计算前将完成所有副作用。

如果第一个操作数的计算结果为 true（非零），则计算第二个操作数。 当逻辑“与”表达式为 false 时，这种计算方式可消除不必要的对第二个操作数的计算。 可以使用此短路计算防止 null 指针取消引用，如以下示例所示：

```cpp
char *pch = 0;
...
(pch) && (*pch = 'a');
```

如果 `pch` 为 null (0)，则从不计算表达式的右侧。 因此，无法通过 null 指针进行赋值。

## <a name="operator-keyword-for-"></a>& & 的运算符关键字

**和**运算符是 **&&** 的文本等效项。 可以通过两种方式在程序中访问**和**运算符：包含头文件 `iso646.h`或使用[/za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展）编译器选项进行编译。

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

[C++内置运算符优先级和结合性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 逻辑运算符](../c-language/c-logical-operators.md)
