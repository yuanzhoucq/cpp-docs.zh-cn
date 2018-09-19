---
title: 编译器错误 C2632 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2632
dev_langs:
- C++
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bf03c35c60bebb52c94ed04cca2349f35c06fbc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093645"
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

若要解决此错误，使代码在 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中有效，重命名标识符。