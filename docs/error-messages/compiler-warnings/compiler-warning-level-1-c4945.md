---
title: 编译器警告（等级 1）C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 15a78877dbe70a7f95674092984546219e6a1c78
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199120"
---
# <a name="compiler-warning-level-1-c4945"></a>编译器警告（等级 1）C4945

"symbol"：无法从 "assembly2" 导入符号：因为 "symbol" 已从另一个程序集 "assembly1" 导入

符号已从引用的程序集导入，但该符号已从另一个引用的程序集导入。 请勿引用其中一个程序集，也不会在其中一个程序集中更改符号名。

下面的示例生成 C4945。

```csharp
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

然后

```csharp
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

然后

```cpp
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```
