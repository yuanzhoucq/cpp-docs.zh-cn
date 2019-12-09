---
title: 编译器错误 C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 093a5856fdcfa6311fcef93214672b035c91b4fc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746521"
---
# <a name="compiler-error-c2513"></a>编译器错误 C2513

"type"：在 "=" 前没有声明变量

类型说明符显示在没有变量标识符的声明中。

下面的示例生成 C2513：

```cpp
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

此错误还可能是由于对 Visual Studio .NET 2003 执行编译器一致性工作引起的：不再允许初始化 typedef。 标准不允许 typedef 的初始化，现在会生成编译器错误。

```cpp
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

另一种方法是删除 `typedef` 来使用聚合初始值设定项列表定义变量，但不建议这样做，因为它将创建与类型同名的变量并隐藏类型名称。
