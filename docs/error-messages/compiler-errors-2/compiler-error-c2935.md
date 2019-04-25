---
title: 编译器错误 C2935
ms.date: 11/04/2016
f1_keywords:
- C2935
helpviewer_keywords:
- C2935
ms.assetid: e11ef90d-0756-4e43-8a09-4974c6aa72a3
ms.openlocfilehash: f44a8060910b1aeeaa4b85d1df081a559e720df8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164886"
---
# <a name="compiler-error-c2935"></a>编译器错误 C2935

“class”：type-class-id 重新定义为全局函数

不能将泛型或模板类用作全局函数。

如果大括号匹配不正确，则可能导致此错误。

以下示例生成 C2935：

```
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

```
// C2935b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC { };
void GC<int>() {}   // C2935
void GC() {}   // OK
```