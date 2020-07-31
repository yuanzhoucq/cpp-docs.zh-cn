---
title: 编译器错误 C3898
ms.date: 11/04/2016
f1_keywords:
- C3898
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
ms.openlocfilehash: e7d1ce25e13e1b601c4abc85e71db484f7b3f822
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221024"
---
# <a name="compiler-error-c3898"></a>编译器错误 C3898

"var"：类型数据成员只能是托管类型的成员

在本机类中声明了[initonly](../../dotnet/initonly-cpp-cli.md)数据成员。  **`initonly`** 数据成员仅可在 CLR 类中声明。

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
