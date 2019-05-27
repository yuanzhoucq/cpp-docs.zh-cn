---
title: 算法（现代 C++）
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
ms.openlocfilehash: b972e575c982ae2523ec560a6237eac76ceaf834
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345173"
---
# <a name="algorithms-modern-c"></a>算法（现代 C++）

在现代 C++ 编程中，建议使用[C++ 标准库](../standard-library/cpp-standard-library-reference.md)中的算法。 下面是一些重要示例：

- **for_each**，为默认遍历算法。 (还**转换**不相称的语义。)

- **find_if**，这是默认的搜索算法。

- **排序**， **lower_bound**，和其他默认排序和搜索算法。

若要写入一个比较运算符，请使用格式精确的 **<** 并在可行时使用*命名的 lambda*。

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="loops"></a>循环

在可行时，请使用基于范围的**for**循环或算法调用，或同时使用两者，而不使用手写的循环。 **copy**、**transform**、 **count_if**、 **remove_if** 和其他类似循环比手写循环要好得多，因为它们的目的很明显，并且使用它们，可以更轻松地编写无 bug 的代码。 此外，许多 C++ 标准库算法具有实现优化，能够使它们更高效。

不使用以下旧 C++ 语法：

```cpp
for ( auto i = strings.begin(); i != strings.end(); ++i ) {
    /* ... */
}

auto i = v.begin();

for ( ; i != v.end(); ++i ) {
    if (*i > x && *i < y) break;
}
```

使用现代 C++ 如下：

```cpp
for_each( begin(strings), end(strings), [](string& s) {
  // ...
} );

auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );
```

### <a name="range-based-for-loops"></a>基于范围的 for 循环

基于范围的 **for** 循环是 C++11 语言功能，而不是C++标准库算法。 但有必要在此有关循环的讨论中予以说明。 基于范围的**for**循环是**for**关键字的一种扩展，并提供一种方便有效的方法来写入可循环访问一系列值的循环。 C++标准库容器、字符串和数组是现成的基于范围的**for**循环。 若要为自定义类型实现此新的迭代语法，请添加以下支持：

- 一个`begin`方法，它将迭代器返回结构的起始位置，以及一个`end`方法，它将迭代器返回结构的结束位置。

- 在迭代器中添加对这些方法的支持：**operator**<strong>\*</strong>，**operator!=**，和**operator++**（前缀版本）。

这些方法可以是成员或独立的函数。

## <a name="random-numbers"></a>随机数字

众所周知，旧 CRT`rand()`函数具有许多缺陷，这一点已在 C++ 社区中被详细讨论。 在新式 C++ 中，无需为这些问题烦恼，也无需构建自己的均匀分布的随机数生成器，因为C++标准库中已提供了可快速轻松创建它们的工具，请参阅[\<random>](../standard-library/random.md)。

## <a name="see-also"></a>请参阅

[欢迎回到 C++（现代 C++）](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)<br/>
