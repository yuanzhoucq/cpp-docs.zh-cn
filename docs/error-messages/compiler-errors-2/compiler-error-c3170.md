---
title: 编译器错误 C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: 5ef39e4580601dd90b5695d9115902bb5b834409
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655684"
---
# <a name="compiler-error-c3170"></a>编译器错误 C3170

不能在项目中具有不同的模块标识符

[模块](../../windows/module-cpp.md)中一次编译中的文件的两个发现了具有不同名称的特性。 只有一个唯一`module`属性可以指定每次编译。

相同`module`属性可以指定多个源代码文件中。

例如，如果发现了以下 module 特性：

```
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

然后，

```
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

编译器将生成 C3170 （请注意不同的名称）。