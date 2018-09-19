---
title: 编译器错误 C3171 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3171
dev_langs:
- C++
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32c58f2ecd9651c347f45c29139ffe0ed65a6e3b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082256"
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