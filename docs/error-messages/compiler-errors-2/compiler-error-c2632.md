---
title: 编译器错误 C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: f69d43bf50f5f13957e49d1e9ffa798a3db5a7b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754688"
---
# <a name="compiler-error-c2632"></a>编译器错误 C2632

"type1" 后跟 "type2" 是非法的

如果两个类型说明符之间缺少代码，可能会导致此错误。

下面的示例生成 C2632：

```cpp
// C2632.cpp
int float i;   // C2632
```

此错误还可能是由于对 Visual Studio .NET 2003 执行的编译器一致性工作而生成的。 `bool` 现在是正确的类型。 在以前的版本中，`bool` 为 typedef，你可以使用该名称创建标识符。

下面的示例生成 C2632：

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

若要解决此错误，使代码在 Visual Studio .NET 2003 和 visual Studio .NET 版本的视觉C++对象中都有效，请重命名标识符。
