---
title: 编译器错误 C2942
ms.date: 11/04/2016
f1_keywords:
- C2942
helpviewer_keywords:
- C2942
ms.assetid: 13abf744-8fa1-450d-886d-e5717c04956e
ms.openlocfilehash: 98bb0d9945068042e00c7c48c0304314e281fa8f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758354"
---
# <a name="compiler-error-c2942"></a>编译器错误 C2942

“class”：type-class-id 重新定义为函数的形参

不能将泛型或模板类用作形参。 不能直接将参数传递到泛型或模板类的构造函数。

下面的示例生成 C2942：

```

// C2942.cpp
// compile with: /c
template<class T>
struct TC {};
void f(int TC<int>) {}   // C2942

// OK
struct TC2 {};
void f(TC2 i) {}
```

使用泛型时也可能发生 C2942：

```cpp
// C2942b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
void f(int GC<int>) {}   // C2942
ref struct GC2 { };
void f(int GC2) {}
```
