---
title: "编译器错误 C3615 |Microsoft 文档"
ms.date: 10/24/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords: C3615
dev_langs: C++
helpviewer_keywords: C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea5502ee6e66cf3add4a4ff97e4922a66712ed70
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3615"></a>编译器错误 C3615

> constexpr 函数*函数*所得结果不能在常量表达式

该函数*函数*可能不会计算为`constexpr`在编译时。 要`constexpr`，函数只能调用其他`constexpr`函数。

## <a name="example"></a>示例

Visual Studio 2017 正确引发错误时有条件地评估操作的左侧操作数不是在中有效`constexpr`上下文。 下面的代码编译 Visual Studio 2015 中但不是在 Visual Studio 2017。

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