---
title: 算法 （现代 C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 604b58f7f8f6074c16effa3220d17bc00c44f5b8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214309"
---
# <a name="algorithms-modern-c"></a>算法（现代 C++）

对于现代 C++ 编程中，我们建议你使用的算法中[C++ 标准库](../standard-library/cpp-standard-library-reference.md)。 下面是一些重要示例：

- **for_each**，为默认遍历算法。 (还**转换**不相称的语义。)

- **find_if**，这是默认的搜索算法。

- **排序**， **lower_bound**，和其他默认排序和搜索算法。

若要写入比较运算符，使用严格**<** 并用*命名的 lambda*时可以。

```cpp  
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );  
```

## <a name="loops"></a>循环

如果可能，请使用基于范围的**为**循环或算法调用，或两者，而不是手写循环。 **复制**，**转换**， **count_if**， **remove_if**，和其他类似是比手写循环要好得多，因为它们的意向都很明显并且它们使其更轻松地编写无 bug 的代码。 此外，许多 C++ 标准库算法具有实现优化，使它们更高效。

而不是旧 C++ 如下：

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

基于范围的**为**循环是 C + + 11 语言功能，不是 c + + 标准库算法。 但值得在本主题中有关循环的说明。 基于范围的**有关**循环是一种扩展的**为**关键字，并提供一种方便有效的方法来写入迭代的循环访问一系列值。 C + + 标准库容器、 字符串和数组是现成的基于范围的**为**循环。 若要启用你的用户定义类型此新迭代语法，请添加以下支持：

- 一个`begin`结构的开头返回一个迭代器方法和一个`end`返回到结构末尾的迭代器的方法。

- 这些方法的迭代器中的支持：**运算符**<strong>\*</strong>，**运算符 ！ =**，并且**operator + +** （前缀版本）。

这些方法可以是成员或独立的函数。

## <a name="random-numbers"></a>随机数字

它是在没有密钥的旧 CRT`rand()`函数具有许多缺陷，具有已详细讨论在 C++ 社区中。 在现代 C++ 中，你不必处理这些不足之处 — 你需要创建你自己均匀分布随机数生成器，也不-中所示，用于快速、轻松地创建它们的工具有可在c++标准库，因为[\<随机 >](../standard-library/random.md)。

## <a name="see-also"></a>请参阅

[欢迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)<br/>
