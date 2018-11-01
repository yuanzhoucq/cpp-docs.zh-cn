---
title: 编译器错误 C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: 602c9ca1051646fca2c5788c036354047fad2522
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599468"
---
# <a name="compiler-error-c3171"></a>编译器错误 C3171

module： 不能在项目中指定不同的模块属性

[模块](../../windows/module-cpp.md)中两个文件在编译时发现了具有不同参数列表的特性。 只有一个唯一`module`属性可以指定每次编译。

相同`module`属性可以指定多个源代码文件中。

例如，如果以下`module`找属性：

```
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

然后，

```
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

编译器将生成 C3171 （请注意不同的版本值）。