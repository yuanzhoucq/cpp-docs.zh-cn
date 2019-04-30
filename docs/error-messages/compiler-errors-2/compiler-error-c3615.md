---
title: 编译器错误 C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: e966295b5ab63350828ddb73d6791a9e30bb5c59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404099"
---
# <a name="compiler-error-c3615"></a>编译器错误 C3615

> constexpr 函数*函数*不会导致一个常量表达式

该函数*函数*可能不会计算为`constexpr`在编译时。 要`constexpr`，一个函数只能调用其他`constexpr`函数。

## <a name="example"></a>示例

Visual Studio 2017 正确引发错误，左操作数的条件性运算中无效时`constexpr`上下文。 下面的代码编译，Visual Studio 2015 中但在 Visual Studio 2017 中不编译。

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

若要解决此问题，请声明`array::size()`充当`constexpr`或删除`constexpr`限定符从`f`。