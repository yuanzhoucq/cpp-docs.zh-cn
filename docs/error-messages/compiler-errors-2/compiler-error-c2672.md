---
title: "编译器错误 C2672 |Microsoft 文档"
ms.date: 10/24/2017
ms.technology:
- cpp-tools
ms.topic: error-reference
f1_keywords:
- C2672
dev_langs:
- C++
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52663aed470aff254d07cba6a65f484269d8703d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2672"></a>编译器错误 C2672

> *函数*： 没有任何匹配重载找到函数

编译器找不到匹配指定的函数的重载的函数。 没有找到函数采用匹配参数或没有匹配的函数在上下文中具有的所需的可访问性。

在由某些标准库容器或算法使用时，你的类型必须提供可访问的成员或满足需求的容器或算法的友元函数。 例如，迭代器类型应派生自`std::iterator<>`。 比较操作或其他运算符上的容器元素类型的使用可能需要类型被视为左侧和右侧的操作数。 因为右操作数可以作为非成员函数的类型需要运算符实现，则使用的类型。

## <a name="example"></a>示例

版本的编译器在 Visual Studio 2017 之前没有执行访问检查某些模板上下文中的限定名称。 这可能会干扰预期的 SFINAE 行为，在这一行为中，预期由于名称的不可访问性，替换会失败。 这可能会导致在运行时发生故障或意外行为，因为编译器错误地调用了运算符的错误重载。 在 Visual Studio 2017 中，引发了编译器错误。

此示例在 Visual Studio 2015 中编译，但引发自 2017 年 Visual Studio 中的错误。 若要解决此问题，请访问的模板参数成员计算位置。

```cpp
#include <type_traits>

template <class T> class S {
// public:    // Uncomment this line to fix
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x)
{
    return (x == 0);
}

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```