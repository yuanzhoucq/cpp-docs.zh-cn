---
title: 编译器错误 C3637
ms.date: 11/04/2016
f1_keywords:
- C3637
helpviewer_keywords:
- C3637
ms.assetid: 72391377-8519-43d9-870a-73a6423deb74
ms.openlocfilehash: c79a4113e20e3798877ccda8f1392b276dee19fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574455"
---
# <a name="compiler-error-c3637"></a>编译器错误 C3637

function： 友元函数定义不能为函数类型的专用化

友元函数模板或泛型定义不正确。

下面的示例生成 C3637:

```
// C3637.cpp
template <class T>
void f();

struct S {
   friend void f<int>() {}   // C3637
};
```

可能的解决方法：

```
// C3637b.cpp
// compile with: /c
template <class T>
void f();

struct S {
   friend void f() {}
};
```

使用泛型时，也可能发生 C3637:

```
// C3637c.cpp
// compile with: /clr

generic <class T>
void gf();

struct S {
   friend void gf<int>() {}   // C3637
};
```

可能的解决方法：

```
// C3637d.cpp
// compile with: /clr /c
generic <class T>
void gf();

struct S {
   friend void gf() {}
};
```