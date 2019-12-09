---
title: 编译器错误 C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: e2d74a637e2902fcf636b49068882f32aa706f94
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761759"
---
# <a name="compiler-error-c3170"></a>编译器错误 C3170

项目中不能有不同的模块标识符

在编译中的两个文件中找到具有不同名称的[模块](../../windows/module-cpp.md)属性。 每个编译只能指定一个唯一的 `module` 属性。

可以在多个源代码文件中指定相同的 `module` 属性。

例如，如果找到以下模块属性：

```cpp
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

然后，

```cpp
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

编译器将生成 C3170 （请注意不同的名称）。
