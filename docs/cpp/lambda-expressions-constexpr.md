---
title: c + + 中的 constexpr lambda 表达式
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: 24c70732093447649b3cfb460f63b2181efdf806
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213341"
---
# <a name="constexpr-lambda-expressions-in-c"></a>c + + 中的 constexpr lambda 表达式

**Visual Studio 2017 版本15.3 及更高版本**（可与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起提供）： **`constexpr`** 在常量表达式中允许对其捕获或引入的每个数据成员进行初始化时，可以将 lambda 表达式声明为或在常量表达式中使用。

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

如果 lambda 的 **`constexpr`** 结果满足函数的要求，则隐式 **`constexpr`** ：

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

如果隐式或显式 lambda **`constexpr`** ，并将其转换为函数指针，则生成的函数也是 **`constexpr`** ：

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C + + 标准库中的函数对象](../standard-library/function-objects-in-the-stl.md)<br/>
[函数调用](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
