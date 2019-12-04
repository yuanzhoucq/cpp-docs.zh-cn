---
title: 编译器错误 C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: a3af19fa6b4f4def9bb42325f648109cfafcdaef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761746"
---
# <a name="compiler-error-c3171"></a>编译器错误 C3171

"module"：在项目中不能指定不同的模块特性

在编译中的两个文件中找到具有不同参数列表的[模块](../../windows/module-cpp.md)属性。 每个编译只能指定一个唯一的 `module` 属性。

可以在多个源代码文件中指定相同的 `module` 属性。

例如，如果找到以下 `module` 属性：

```cpp
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

然后，

```cpp
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

编译器将生成 C3171 （请注意不同版本的值）。
