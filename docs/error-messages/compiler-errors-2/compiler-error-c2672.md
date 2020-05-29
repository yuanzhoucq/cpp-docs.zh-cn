---
title: 编译器错误 C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: 9f844b54285a7df69bfb4387a7afcc82dfef9252
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177126"
---
# <a name="compiler-error-c2672"></a>编译器错误 C2672

> "*function*"：未找到匹配的重载函数

编译器找不到与指定函数匹配的重载函数。 找不到采用匹配参数的函数，或者没有任何匹配的函数在上下文中具有所需的可访问性。

当由某些标准库容器或算法使用时，你的类型必须提供满足容器或算法的要求的可访问成员或友元函数。 例如，迭代器类型应派生自 `std::iterator<>`。 在容器元素类型上进行比较运算或使用其他运算符时，可能需要将类型视为左操作数和右操作数。 将类型用作右侧操作数可能需要将运算符作为类型的非成员函数来实现。

## <a name="example"></a>示例

Visual Studio 2017 之前的编译器版本未对某些模板上下文中的限定名称执行访问检查。 这可能会干扰预期的 SFINAE 行为，在这一行为中，预期由于名称的不可访问性，替换会失败。 这可能会导致在运行时发生故障或意外行为，因为编译器错误地调用了运算符的错误重载。 在 Visual Studio 2017 中，引发了编译器错误。

此示例在 Visual Studio 2015 中进行编译，但在 Visual Studio 2017 中引发错误。 若要解决此问题，请使模板参数成员在计算时可以访问。

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
