---
title: 编译器警告（等级1） C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 6a20effcebe1a36fa1356fffefa3a23a0056a0f0
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052260"
---
# <a name="compiler-warning-level-1-c4945"></a>编译器警告（等级1） C4945

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