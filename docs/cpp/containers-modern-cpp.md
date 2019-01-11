---
title: 容器（现代 C++）
ms.date: 1/18/2018
ms.topic: conceptual
ms.openlocfilehash: 2da57bfca8b04f50a223dddfb886835c69f746a4
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220135"
---
# <a name="containers-modern-c"></a>容器（现代 C++）

默认情况下，使用[向量](../standard-library/vector-class.md)作为 C++ 中的首选顺序容器。 这相当于`List<T>`用.NET 语言。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

使用[地图](../standard-library/map-class.md)(不`unordered_map`) 作为默认关联容器。 使用[设置](../standard-library/set-class.md)，[多重映射](../standard-library/multimap-class.md)，并[多重集](../standard-library/multiset-class.md)退化 & 多用例。

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

当需要性能优化时，请考虑使用：

- [数组](../standard-library/array-class-stl.md)键入时嵌入是重要的是，例如，作为类成员。

- 如无序的关联容器[unordered_map](../standard-library/unordered-map-class.md)。 这些开销具有较低的每个元素和常数时间查找，但它们可能很难正确有效地使用。

- 排序`vector`。 有关详细信息，请参阅[算法](../cpp/algorithms-modern-cpp.md)。

不要使用 C 样式数组。 对于需要直接访问数据的较旧的 Api，使用访问器方法如`f(vec.data(), vec.size());`相反。

有关容器的详细信息，请参阅[C++ 标准库容器](../standard-library/stl-containers.md)。

## <a name="see-also"></a>请参阅

[欢迎回到 C++（现代 C++）](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
