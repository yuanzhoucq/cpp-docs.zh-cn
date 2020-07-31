---
title: 编译器错误 C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: 17a210e2a514af1ffd62bf38651c4d17bd1fe32b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230787"
---
# <a name="compiler-error-c3615"></a>编译器错误 C3615

> constexpr 函数 "*function*" 不能导致常量表达式

函数*函数*在编译时无法计算为 **`constexpr`** 。 为 **`constexpr`** ，函数只能调用其他 **`constexpr`** 函数。

## <a name="example"></a>示例

当条件计算操作的左操作数在上下文中无效时，Visual Studio 2017 正确引发错误 **`constexpr`** 。 下面的代码在 Visual Studio 2015 中进行编译，但在 Visual Studio 2017 中未进行编译。

```cpp
// C3615.cpp
// Compile with: /c

template<int N>
struct myarray
{
    int size() const { return N; }
};

constexpr bool f(const myarray<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615 starting in Visual Studio 2017
}
```

若要解决此问题，请将 `array::size()` 函数声明为， **`constexpr`** 或者 **`constexpr`** 从中删除该限定符 `f` 。
