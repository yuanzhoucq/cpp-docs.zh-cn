---
title: 基于范围的 for 语句 (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: af9811fd707d4dbc28158dba3b6b3fbfcc43e4fe
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077182"
---
# <a name="range-based-for-statement-c"></a>基于范围的 for 语句 (C++)

对 `statement` 中的每个元素按顺序重复执行 `expression`。

## <a name="syntax"></a>语法

```
for ( for-range-declaration : expression )
   statement
```

## <a name="remarks"></a>备注

使用基于范围**的 for**语句来构造必须通过 "范围" 执行的循环，该循环定义为可循环访问的任何内容（例如 `std::vector`或任何其他C++标准库序列，其范围由 `begin()` 和 `end()`定义）。 `for-range-declaration` 部分中声明的名称是**for**语句的本地名称，不能在 `expression` 或 `statement`中重新声明。 请注意，在语句的 `for-range-declaration` 部分中， [auto](../cpp/auto-cpp.md)关键字是首选的。

**Visual Studio 2017 中的新增内容：** 基于范围的 for 循环不再需要 begin （）和 end （）返回相同类型的对象。 这使得 end() 能够返回类似于 Ranges-V3 方案中定义的 ranges 所使用的那种 sentinel 对象。 有关详细信息，请参阅 [Generalizing the Range-Based For Loop](https://wg21.link/p0184r0)（通用化基于范围的 for 循环）和 [range-v3 library on GitHub](https://github.com/ericniebler/range-v3)（GitHub 上的 range-v3 库）。

此代码演示如何使用基于范围**的 for**循环来循环访问数组和向量：

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

执行 `statement` 中的其中一项时，基于范围**的 for**循环将终止：在基于范围**的 for**循环外部的标记语句的[break](../cpp/break-statement-cpp.md)、 [return](../cpp/return-statement-cpp.md)或[goto](../cpp/goto-statement-cpp.md) 。 基于范围**的 for**循环中的[continue](../cpp/continue-statement-cpp.md)语句仅终止当前迭代。

请记住以下有关基于范围**的**内容：

- 自动识别数组。

- 识别拥有 `.begin()` 和 `.end()` 的容器。

- 对于任何其他内容，使用依赖于自变量的查找 `begin()` 和 `end()`。

## <a name="see-also"></a>另请参阅

[auto](../cpp/auto-cpp.md)<br/>
[迭代语句](../cpp/iteration-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[while 语句 (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while 语句 (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for 语句 (C++)](../cpp/for-statement-cpp.md)