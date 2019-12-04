---
title: 编译器错误 C2935
ms.date: 11/04/2016
f1_keywords:
- C2935
helpviewer_keywords:
- C2935
ms.assetid: e11ef90d-0756-4e43-8a09-4974c6aa72a3
ms.openlocfilehash: 676c238dfb0ae78dbe5b144b5242bfb4ccbda76c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756144"
---
# <a name="compiler-error-c2935"></a>编译器错误 C2935

“class”：type-class-id 重新定义为全局函数

不能将泛型或模板类用作全局函数。

如果大括号匹配不正确，则可能导致此错误。

以下示例生成 C2935：

```cpp
// C2935.cpp
// compile with: /c
template<class T>
struct TC {};
void TC<int>() {}   // C2935

// OK
struct TC2 {};
void TC2() {}
```

使用泛型时也可能发生 C2935：

```cpp
// C2935b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC { };
void GC<int>() {}   // C2935
void GC() {}   // OK
```
