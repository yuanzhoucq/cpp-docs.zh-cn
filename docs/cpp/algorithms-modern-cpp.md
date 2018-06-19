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
ms.openlocfilehash: fdd5742bb86992ce20f5a52f587c8557d46a97eb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412291"
---
# <a name="algorithms-modern-c"></a>算法（现代 C++）
对于现代 C++ 编程中，我们建议你使用的算法中[C++ 标准库](../standard-library/cpp-standard-library-reference.md)。 下面是一些重要示例：  
  
-   `for_each`这是默认的遍历算法。 (还`transform`not 的就地语义。)  
  
-   `find_if`这是默认的搜索算法。  
  
-   `sort``lower_bound`，以及其他默认排序和搜索算法。  
  
 若要编写比较器，使用严格`<`并用*名为 lambda*何时可以。  
  
```cpp  
auto comp = [](const widget& w1, const widget& w2)  
      { return w1.weight() < w2.weight(); }  
  
sort( v.begin(), v.end(), comp );  
  
auto i = lower_bound( v.begin(), v.end(), comp );  
```  
  
## <a name="loops"></a>循环  
 如果可能，请使用基于范围的`for`循环算法调用和 / 或，而不是手动编写循环。`copy`， `transform`， `count_if`， `remove_if`，和其他类型像它们是比手写循环因为及其意图是明显的并且可以使用户更轻松地编写无 bug 的代码。 此外，许多 C++ 标准库算法具有实现优化，使它们更高效。  
  
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
 基于范围的`for`循环是 C++ 11 语言功能，不是 C++ 标准库算法。 但值得在本主题中有关循环的说明。 基于范围的`for`循环是一种扩展的`for`关键字并提供方便且高效的方式来编写循环访问一系列值的循环。 C++ 标准库容器、 字符串和数组是现成的基于范围的`for`循环。 若要启用你的用户定义类型此新迭代语法，请添加以下支持：  
  
-   A`begin`返回结构的开头的迭代器的方法和`end`结构末尾返回的迭代器的方法。  
  
-   这些方法的迭代器中的支持： `operator*`， `operator!=`，和`operator++`（前缀版本）。  
  
 这些方法可以在成员或独立函数。  
  
## <a name="random-numbers"></a>随机数  
 它是在没有密钥的旧 CRT`rand()`函数具有许多缺陷，具有已详细讨论在 C++ 社区中。 在现代 C++ 中，你不必处理这些不足之处 — 你需要创建你自己均匀分布随机数生成器，也不-中所示，用于快速、轻松地创建它们的工具有可在c++标准库，因为[\<随机 >](../standard-library/random.md)。  
  
## <a name="see-also"></a>请参阅  
 [欢迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C++ 语言参考](../cpp/cpp-language-reference.md)   
 [C++ 标准库](../standard-library/cpp-standard-library-reference.md)