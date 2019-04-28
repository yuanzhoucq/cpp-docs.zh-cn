---
title: 编译器错误 C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: b92d44bcfd04d4de7b39c5bdab5ee146d9b6693b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257629"
---
# <a name="compiler-error-c2632"></a>编译器错误 C2632

type1 和 type2 是非法的

如果缺少两个类型说明符之间的代码可以导致此错误。

下面的示例生成 C2632:

```
// C2632.cpp
int float i;   // C2632
```

为 Visual Studio.NET 2003年执行的编译器一致性工作，还可以生成此错误。 `bool` 现在是正确的类型。 在以前版本， `bool` typedef，您可以创建具有该名称的标识符。

下面的示例生成 C2632:

```
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

若要解决此错误，以便代码是有效的 Visual Studio.NET 2003年和 Visual Studio.NET 版本的视觉对象中的C++，重命名标识符。