---
title: 编译器错误 C3898
ms.date: 11/04/2016
f1_keywords:
- C3898
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
ms.openlocfilehash: 02c649fb906b0c5f09afe25952a8670c1a0e7f3d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749199"
---
# <a name="compiler-error-c3898"></a>编译器错误 C3898

"var"：类型数据成员只能是托管类型的成员

在本机类中声明了[initonly](../../dotnet/initonly-cpp-cli.md)数据成员。  `initonly` 数据成员仅可在 CLR 类中声明。

下面的示例生成 C3898：

```cpp
// C3898.cpp
// compile with: /clr
struct Y1 {
   initonly
   static int data_var = 9;   // C3898
};
```

可能的解决方法：

```cpp
// C3898b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int data_var = 9;
};
```
