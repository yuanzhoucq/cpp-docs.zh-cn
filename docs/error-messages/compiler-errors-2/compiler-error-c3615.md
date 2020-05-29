---
title: 编译器错误 C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: c1a5b6edbc87e14de267cf962dc2b1a71dd6be12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200533"
---
# <a name="compiler-error-c3615"></a>编译器错误 C3615

> constexpr 函数 "*function*" 不能导致常量表达式

函数*函数*在编译时无法计算为 `constexpr`。 若要 `constexpr`，函数只能调用其他 `constexpr` 函数。

## <a name="example"></a>示例

当条件计算操作的左操作数在 `constexpr` 上下文中无效时，Visual Studio 2017 正确引发错误。 下面的代码在 Visual Studio 2015 中进行编译，但在 Visual Studio 2017 中未进行编译。

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

若要解决此问题，请将 `array::size()` 函数声明为 `constexpr` 或删除 `f`中的 `constexpr` 限定符。
