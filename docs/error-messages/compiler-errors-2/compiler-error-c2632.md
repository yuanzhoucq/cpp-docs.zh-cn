---
title: 编译器错误 C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: 8ea3a106e8819bf067203f220ca51e17b87bfe46
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225457"
---
# <a name="compiler-error-c2632"></a>编译器错误 C2632

"type1" 后跟 "type2" 是非法的

如果两个类型说明符之间缺少代码，可能会导致此错误。

下面的示例生成 C2632：

```cpp
// C2632.cpp
int float i;   // C2632
```

此错误还可能是由于对 Visual Studio .NET 2003 执行的编译器一致性工作而生成的。 **`bool`** 现在是正确的类型。 在以前的版本中， **`bool`** 为 typedef，你可以使用该名称创建标识符。

下面的示例生成 C2632：

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

若要解决此错误，使代码在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++ 中都有效，请重命名标识符。
