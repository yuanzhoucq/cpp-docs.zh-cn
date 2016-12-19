---
title: "算法（现代 C++） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 算法（现代 C++）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

针对现代 C\+\+ 编程，建议您使用[标准模板库](../standard-library/cpp-standard-library-reference.md) \(STL\) 中的算法。  以下是一些重要示例：  
  
-   `for_each` 为默认遍历算法。（还 `transform` 不相称的语义。）  
  
-   `find_if` 为默认搜索算法。  
  
-   `sort`、`lower_bound` 和其他默认值排序和搜索算法。  
  
 若要写入比较运算符，则在可能的情况下请使用严格的 `<` 和使用“命名的 lambda”。  
  
```cpp  
  
auto comp = [](const widget& w1, const widget& w2)  
      { return w1.weight() < w2.weight(); }  
  
sort( v.begin(), v.end(), comp );  
  
auto i = lower_bound( v.begin(), v.end(), comp );  
  
```  
  
## 循环  
 如果可能，请使用基于范围的 `for` 循环或算法调用，或同时使用两者，而非手写循环。  `copy`、`transform`、`count_if`、`remove_if` 以及其他类似的都比手写循环要好得多，因为它们的意向都很明显并且它们让编写无 bug 的代码变得更容易。  此外，许多 STL 算法都有使它们更高效的实现优化。  
  
 而不使用这样的旧 C\+\+：  
  
```cpp  
  
for( auto i = strings.begin(); i != strings.end(); ++i ) {  
  :::  
  :::  
}  
  
auto i = v.begin();  
  
for( ; i != v.end(); ++i ) {  
  if (*i > x && *i < y) break;  
}  
  
```  
  
 使用如下的现代 C\+\+：  
  
```cpp  
  
for_each( begin(strings), end(strings), [](string& s) {  
  :::  
  :::  
} );  
auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; }  );  
  
```  
  
### 基于范围的 for 循环  
 基于范围的 `for` 循环是 c. \+\+11 语言功能，而不是 STL 算法。  但是需要在关于循环的讨论中提到它。  基于范围的 `for` 循环是 `for` 关键字的扩展并提供一种方便有效方法来写入迭代多个值的循环。  STL 容器、字符串和数组对于基于范围的 `for` 循环是现成的。  若要为用户定义的类型启用此新的迭代语法，请添加以下支持：  
  
-   将迭代器返回到结构开始的 `begin` 方法和将迭代器返回到结构末尾的 `end` 方法。  
  
-   迭代器中支持以下方法：`operator*`、`operator!=` 和 `operator++`（前缀版本）。  
  
 这些方法可以是成员或单独存在的函数。  
  
## 随机数字  
 众所周知旧 CRT `rand()` 函数具有许多缺点，这在 C\+\+ 社区中已进行了完整讨论。  在现代 C\+\+，您不必处理这些不足，也无须发明您自己统一分发的随机数生成器，因为快速轻松地创建它们的工具可在 STL 中获得，如 [\<random\>](../standard-library/random.md) 所示。  
  
## 请参阅  
 [欢迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)