---
title: '逻辑 OR 运算符: | |'
ms.date: 06/14/2018
f1_keywords:
- '||'
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 5db1af870644d1552aeac813edce0985a31d95b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368677"
---
# <a name="logical-or-operator-"></a>逻辑 OR 运算符: | |

## <a name="syntax"></a>语法

> *logical-or-expression* **||** *logical-and-expression*

## <a name="remarks"></a>备注

逻辑 OR 运算符 (**||**) 返回布尔值为 TRUE，如果一个或两个操作数为 TRUE，否则返回 FALSE。 操作数隐式转换为类型**bool**之前的评估，并将该结果属于类型**bool**。 逻辑“或”具有从左向右的关联性。

逻辑“或”运算符的操作数不需要是同一类型，但是它们必须是整型或指针类型。 操作数通常为关系或相等表达式。

第一个操作数将完全计算，并且在继续计算逻辑“或”表达式之前将完成所有副作用。

仅当第一个操作数的计算结果为 false (0) 时计算第二个操作数。 在逻辑“或”表达式为 true 时，这将消除对第二个操作数的不必要的计算。

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

在上面的示例中，如果 `x` 与 `w`、`y` 或 `z` 相等，则 `printf` 函数的第二个自变量的计算结果将为 true，并打印值 1。 否则，它的计算结果将为 false，并打印值 0。 只要其中一个条件的计算结果为 true，计算便会停止。

## <a name="operator-keyword-for-124124"></a>运算符关键字&#124;&#124;

**或**运算符是的文本等效**||**。 有两种方法来访问**或**您的程序中的运算符： 包含头文件\<iso646.h >，或使用编译[/Za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展） 编译器选项。

## <a name="example"></a>示例

```cpp
// expre_Logical_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate logical OR
#include <iostream>
using namespace std;
int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b || b > c yields "
         << (a < b || b > c) << endl
         << "The false expression "
         << "a > b || b > c yields "
         << (a > b || b > c) << endl;
}
```

## <a name="see-also"></a>请参阅

[C++内置运算符优先级和结合性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 逻辑运算符](../c-language/c-logical-operators.md)