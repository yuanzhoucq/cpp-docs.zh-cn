---
title: break 语句 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- break_cpp
dev_langs:
- C++
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99b342719593b2072cdba21e3200aa23daa8f9df
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087274"
---
# <a name="break-statement-c"></a>break 语句 (C++)

**中断**语句将终止执行最近的封闭循环或它所在的条件语句。 控制权将传递给该语句结束之后的语句（如果有的话）。

## <a name="syntax"></a>语法

```
break;
```

## <a name="remarks"></a>备注

**中断**语句用于条件性[切换](../cpp/switch-statement-cpp.md)语句且[执行](../cpp/do-while-statement-cpp.md)，[对于](../cpp/for-statement-cpp.md)，和[时](../cpp/while-statement-cpp.md)循环语句。

在中**切换**语句**中断**语句会导致要执行的下一个语句之外的程序**切换**语句。 无需**中断**语句中，每个语句从匹配**用例**到末尾的标签**切换**语句，包括**默认**子句中，执行。

在循环中，**中断**语句将终止执行最近的封闭**做**，**有关**，或**而**语句。 控制权将传递给终止语句之后的语句（如果有的话）。

在嵌套语句**中断**语句只终止**执行**，**有关**，**切换**，或**时**直接包围它的语句。 可以使用**返回**或**goto**语句将控制权从较深嵌套的结构。

## <a name="example"></a>示例

下面的代码演示如何使用**中断**中的语句**为**循环。

```cpp
#include <iostream>
using namespace std;

int main()
{
    // An example of a standard for loop
    for (int i = 1; i < 10; i++)
    {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }

    // An example of a range-based for loop
int nums []{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

    for (int i : nums) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }
}
```

```Output
In each case:
1
2
3
```

下面的代码演示如何使用**中断**中**虽然**循环和一个**执行**循环。

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;

    while (i < 10) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    }

    i = 0;
    do {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    } while (i < 10);
}
```

```Output
In each case:
0123
```

下面的代码演示如何使用**中断**switch 语句中。 必须使用**中断**在所有情况下，如果你想要处理每种情况下，单独; 如果不使用**中断**，代码则执行下一用例。

```cpp
#include <iostream>
using namespace std;

enum Suit{ Diamonds, Hearts, Clubs, Spades };

int main() {

    Suit hand;
    . . .
    // Assume that some enum value is set for hand
    // In this example, each case is handled separately
    switch (hand)
    {
    case Diamonds:
        cout << "got Diamonds \n";
        break;
    case Hearts:
        cout << "got Hearts \n";
        break;
    case Clubs:
        cout << "got Clubs \n";
        break;
    case Spades:
        cout << "got Spades \n";
        break;
    default:
          cout << "didn't get card \n";
    }
    // In this example, Diamonds and Hearts are handled one way, and
    // Clubs, Spades, and the default value are handled another way
    switch (hand)
    {
    case Diamonds:
    case Hearts:
        cout << "got a red card \n";
        break;
    case Clubs:
    case Spades:
    default:
        cout << "didn't get a red card \n";
    }
}
```

## <a name="see-also"></a>请参阅

[跳转语句](../cpp/jump-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[continue 语句](../cpp/continue-statement-cpp.md)