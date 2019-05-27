---
title: 容器（现代 C++）
ms.date: 1/18/2018
ms.topic: conceptual
ms.openlocfilehash: 2da57bfca8b04f50a223dddfb886835c69f746a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392331"
---
# <a name="containers-modern-c"></a>容器（现代 C++）

默认情况下，使用[向量](../standard-library/vector-class.md)作为 C++ 中的首选顺序容器。 这等同于.NET 语言中的`List<T>`。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

使用[map](../standard-library/map-class.md)（而不是`unordered_map`）作为默认关联容器。 对于 degenerate 和 multi 的情况，使用[set](../standard-library/set-class.md)，[multimap](../standard-library/multimap-class.md)和[multiset](../standard-library/multiset-class.md)。

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

当需要性能优化时，请考虑使用：

- [数组](../standard-library/array-class-stl.md)，前提是当嵌入很重要时，例如，作为类成员。

- 无序的关联容器，例如[unordered_map](../standard-library/unordered-map-class.md)。 这些容器具有较低的元素开销和定时查找特性，但可能很难正确有效地使用它们。

- 经过排序的`vector`。 有关详细信息，请参阅[算法](../cpp/algorithms-modern-cpp.md)。

不要使用 C 样式数组。 对于需要直接访问数据的较旧的 Api，请使用访问器方法，如`f(vec.data(), vec.size());`。

有关容器的详细信息，请参阅[C++ 标准库容器](../standard-library/stl-containers.md)。

## <a name="see-also"></a>请参阅

[欢迎回到 C++（现代 C++）](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
