---
title: 编译器警告（等级 1）C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 62dfbaed28f1afcdedb41d83158dfe4e8e0f61b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653851"
---
# <a name="compiler-warning-level-1-c4945"></a>编译器警告（等级 1）C4945

symbol： 无法导入 assembly2 中的符号： 因为 symbol 具有已导入从另一个程序集 assembly1

从引用的程序集导入一个符号，但该符号从另一个引用的程序集导入。 请勿引用某个程序集，或者更改其中一个程序集的符号名称。

以下示例生成 C4945。

```
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

然后

```
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

然后

```
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```