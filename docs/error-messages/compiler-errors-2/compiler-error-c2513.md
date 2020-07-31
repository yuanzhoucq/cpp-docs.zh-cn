---
title: 编译器错误 C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 96f2ccc29eed5c1fa4e29f69d18ae6503417f211
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212717"
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

另一种方法是删除 **`typedef`** 以使用聚合初始值设定项列表定义变量，但不建议这样做，因为它将创建一个与类型同名的变量并隐藏类型名称。
