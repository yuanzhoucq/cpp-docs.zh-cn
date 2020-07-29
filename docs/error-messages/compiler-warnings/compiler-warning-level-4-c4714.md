---
title: 编译器警告（等级 4）C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: 286a9e6e12643d3dadd070e7c4cf4b2dd350c02c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219854"
---
# <a name="compiler-warning-level-4-c4714"></a>编译器警告（等级 4）C4714

> 标记为 __forceinline 的函数 "function" 未内联

为内联展开选择了给定函数，但编译器未执行内联。

尽管 **`__forceinline`** 是编译器的更强指示 **`__inline`** ，但仍会自行自行执行内联，但不会使用试探法来确定内联此函数所带来的好处。

在某些情况下，编译器不会出于机械原因而内联特定函数。 例如，编译器不会内联：

- 如果该函数导致同时混合 SEH 和 c + + EH，则为。

- 当-GX/EHs/EHa 为 on 时，某些函数具有按值传递的复制构造对象。

- 当-GX/EHs/EHa 为 on 时，函数按值返回不可展开对象。

- 在不包含-Og/Ox/O1/O2 的情况下编译时具有内联程序集的函数。

- 带有变量参数列表的函数。

- 具有 **`try`** （c + + 异常处理）语句的函数。

下面的示例生成 C4714：

```cpp
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```
