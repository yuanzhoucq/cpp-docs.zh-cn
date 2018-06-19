---
title: 容器 （现代 C++） |Microsoft 文档
ms.custom: ''
ms.date: 1/18/2018
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49a77234b679fd61d801bb78d751891467d6b4e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412070"
---
# <a name="containers-modern-c"></a>容器（现代 C++）

默认情况下，使用[向量](../standard-library/vector-class.md)作为 C++ 中的首选顺序容器。 这相当于`List<T>`.NET 语言。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

使用[映射](../standard-library/map-class.md)(不`unordered_map`) 作为默认关联容器。 使用[设置](../standard-library/set-class.md)，[多重映射](../standard-library/multimap-class.md)，和[多重集](../standard-library/multiset-class.md)退化和多用例。

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

当需要性能优化时，请考虑使用：

- [数组](../standard-library/array-class-stl.md)键入嵌入十分重要，例如，作为类成员时。

- 如无序的关联容器[unordered_map](../standard-library/unordered-map-class.md)。 这些开销具有较低的每个元素，并且常量时间查找，但它们可以作为难以正确有效地使用。

- 排序**向量**。 有关详细信息，请参阅[算法](../cpp/algorithms-modern-cpp.md)。

不要使用 C 样式数组。 对于需要直接访问数据的较旧 Api，使用访问器方法如`f(vec.data(), vec.size());`相反。

有关容器的详细信息，请参阅[C++ 标准库容器](../standard-library/stl-containers.md)。

## <a name="see-also"></a>请参阅

[欢迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)  
[C++ 语言参考](../cpp/cpp-language-reference.md)  
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)  
