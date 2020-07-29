---
title: 基于范围的 for 语句 (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: 1197080e2e96e0e5c51bc06e93026567a33c7842
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223611"
---
# <a name="range-based-for-statement-c"></a>基于范围的 for 语句 (C++)

对 `statement` 中的每个元素按顺序重复执行 `expression`。

## <a name="syntax"></a>语法

> **`for (`***对于范围声明* **`:`***表达式***`)`**\
&emsp;*语句*

## <a name="remarks"></a>备注

使用基于范围的 **`for`** 语句来构造必须通过*范围*执行的循环，该范围定义为可循环访问的任何内容，例如， `std::vector` 或其范围由和定义的任何其他 c + + 标准库序列 `begin()` `end()` 。 部分中声明的名称 `for-range-declaration` 是语句的本地名称 **`for`** ，不能在或中重新声明 `expression` `statement` 。 请注意，在 [`auto`](../cpp/auto-cpp.md) 语句的部分中，关键字是首选的 `for-range-declaration` 。

**Visual Studio 2017 中的新增内容：** 基于范围的 **`for`** 循环不再要求 `begin()` 和 `end()` 返回相同类型的对象。 这允许 `end()` 返回一个 sentinel 对象，如范围-V3 建议中定义的范围所使用的。 有关详细信息，请参阅 GitHub 上[的通用化基于范围的 `For` 循环](https://wg21.link/p0184r0)和[范围-v3 库](https://github.com/ericniebler/range-v3)。

此代码演示如何使用基于范围的 **`for`** 循环来循环访问数组和向量：

```cpp
// range-based-for.cpp
// compile by using: cl /EHsc /nologo /W4
#include <iostream>
#include <vector>
using namespace std;

int main()
{
    // Basic 10-element integer array.
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

    // Range-based for loop to iterate through the array.
    for( int y : x ) { // Access by value using a copy declared as a specific type.
                       // Not preferred.
        cout << y << " ";
    }
    cout << endl;

    // The auto keyword causes type inference to be used. Preferred.

    for( auto y : x ) { // Copy of 'x', almost always undesirable
        cout << y << " ";
    }
    cout << endl;

    for( auto &y : x ) { // Type inference by reference.
        // Observes and/or modifies in-place. Preferred when modify is needed.
        cout << y << " ";
    }
    cout << endl;

    for( const auto &y : x ) { // Type inference by const reference.
        // Observes in-place. Preferred when no modify is needed.
        cout << y << " ";
    }
    cout << endl;
    cout << "end of integer array test" << endl;
    cout << endl;

    // Create a vector object that contains 10 elements.
    vector<double> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(i + 0.14159);
    }

    // Range-based for loop to iterate through the vector, observing in-place.
    for( const auto &j : v ) {
        cout << j << " ";
    }
    cout << endl;
    cout << "end of vector test" << endl;
}
```

输出如下：

```Output
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
end of integer array test

0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159
end of vector test
```

**`for`** 当执行以下中的其中一项时，基于范围的循环将终止 `statement` ：将 [`break`](../cpp/break-statement-cpp.md) 、 [`return`](../cpp/return-statement-cpp.md) 或 [`goto`](../cpp/goto-statement-cpp.md) 添加到基于范围的循环之外的标记语句中 **`for`** 。 [`continue`](../cpp/continue-statement-cpp.md)基于范围的循环中的语句 **`for`** 仅终止当前迭代。

请记住以下有关基于范围的 **`for`** 内容：

- 自动识别数组。

- 识别拥有 `.begin()` 和 `.end()` 的容器。

- 对于任何其他内容，使用依赖于自变量的查找 `begin()` 和 `end()`。

## <a name="see-also"></a>另请参阅

[`auto`](../cpp/auto-cpp.md)<br/>
[迭代语句](../cpp/iteration-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[`while`语句 (C++)](../cpp/while-statement-cpp.md)<br/>
[`do-while`语句 (C++)](../cpp/do-while-statement-cpp.md)<br/>
[`for`语句 (C++)](../cpp/for-statement-cpp.md)
