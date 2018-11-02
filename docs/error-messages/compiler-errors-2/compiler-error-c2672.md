---
title: 编译器错误 C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: df0f656c9db23739ec62629088b9cc5f7950a92d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570438"
---
# <a name="compiler-error-c2672"></a>编译器错误 C2672

> '*函数*： 没有匹配的重载函数找到

编译器找不到匹配指定的函数的重载的函数。 没有函数找到匹配的参数或没有匹配的函数采用在上下文中具有所需的可访问性。

由某些标准库容器或算法，您的类型必须提供可访问的成员或满足需求的容器或算法的友元函数。 例如，您的迭代器类型应派生自`std::iterator<>`。 比较操作或对容器元素类型的其他运算符的使用可能需要类型被视为左和右操作数。 右操作数可以要求为类型的非成员函数运算符实现类型使用。

## <a name="example"></a>示例

版本的编译器 Visual Studio 2017 之前未执行访问检查某些模板上下文中的限定名称。 这可能会干扰预期的 SFINAE 行为，在这一行为中，预期由于名称的不可访问性，替换会失败。 这可能会导致在运行时发生故障或意外行为，因为编译器错误地调用了运算符的错误重载。 在 Visual Studio 2017 中，引发了编译器错误。

此示例在 Visual Studio 2015 中编译，但引发 Visual Studio 2017 中的错误。 若要解决此问题，使可访问该模板参数成员在计算。

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