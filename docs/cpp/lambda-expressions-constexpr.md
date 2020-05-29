---
title: 中的 constexpr lambda 表达式C++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: 9467d9e404204012df6461adacd5dc4cdbdfe71d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179570"
---
# <a name="constexpr-lambda-expressions-in-c"></a>中的 constexpr lambda 表达式C++

**Visual Studio 2017 版本15.3 及更高版本**（可与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起提供）： lambda 表达式可以声明为**constexpr** ，或在常量表达式中允许其捕获或引入的每个数据成员的初始化时在常数表达式中使用。

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

如果 lambda 的结果满足**constexpr**函数的要求，则它会隐式**constexpr** ：

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

如果 lambda 为隐式或显式**constexpr**，并将其转换为函数指针，则生成的函数也是**constexpr**：

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>另请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库中的函数对象](../standard-library/function-objects-in-the-stl.md)<br/>
[函数调用](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
