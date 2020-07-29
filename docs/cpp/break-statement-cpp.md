---
title: break 语句 (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 30ca602ecc65099adff7300f730c500a31fe0ed5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227603"
---
# <a name="break-statement-c"></a>break 语句 (C++)

**`break`** 语句结束执行最近的封闭循环或它所在的条件语句。 控制权将传递给该语句结束之后的语句（如果有的话）。

## <a name="syntax"></a>语法

```
break;
```

## <a name="remarks"></a>备注

**`break`** 语句与条件[switch](../cpp/switch-statement-cpp.md)语句一起使用，并且带有[do](../cpp/do-while-statement-cpp.md)、 [for](../cpp/for-statement-cpp.md)和[while](../cpp/while-statement-cpp.md)循环语句。

在 **`switch`** 语句中， **`break`** 语句导致程序执行语句外的下一个语句 **`switch`** 。 如果没有 **`break`** 语句，则将执行从匹配的 **`case`** 标签到语句末尾的每个语句 **`switch`** ，包括 **`default`** 子句。

在循环中， **`break`** 语句结束执行最近的封闭 **`do`** 、 **`for`** 或 **`while`** 语句。 控制权将传递给终止语句之后的语句（如果有的话）。

在嵌套语句中， **`break`** 语句只结束 **`do`** **`for`** 直接括起来的、、 **`switch`** 或 **`while`** 语句。 您可以使用 **`return`** 或 **`goto`** 语句从更深层嵌套的结构中传输控件。

## <a name="example"></a>示例

下面的代码演示如何 **`break`** 在循环中使用语句 **`for`** 。

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

下面的代码演示如何 **`break`** 在 **`while`** 循环和循环中使用 **`do`** 。

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

下面的代码演示如何 **`break`** 在 switch 语句中使用。 **`break`** 如果要分别处理每个大小写，则必须在每种情况下使用; 如果不使用 **`break`** ，则代码执行将贯穿到下一种情况。

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

## <a name="see-also"></a>另请参阅

[跳转语句](../cpp/jump-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[continue 语句](../cpp/continue-statement-cpp.md)
