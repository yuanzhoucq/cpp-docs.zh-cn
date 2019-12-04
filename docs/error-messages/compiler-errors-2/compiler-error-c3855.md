---
title: 编译器错误 C3855
ms.date: 11/04/2016
f1_keywords:
- C3855
helpviewer_keywords:
- C3855
ms.assetid: ed90f8c0-4154-4243-b066-493913df5727
ms.openlocfilehash: 226f87ad428e9f005e36823834cedc2b3ee0b8c6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754818"
---
# <a name="compiler-error-c3855"></a>编译器错误 C3855

"class"：类型参数 "param" 与声明不兼容

编译器找到了非参数模板或具有不同名称的泛型参数。 当模板特殊化定义中的指定模板参数与其声明不兼容时，可能会出现这种情况。

下面的示例生成 C3855：

```cpp
// C3855.cpp
template <int N>
struct C {
   void f();
};

template <char N>
void C<N>::f() {}   // C3855
```

可能的解决方法：

```cpp
// C3855b.cpp
// compile with: /c
template <int N>
struct C {
   void f();
};

template <int N>
void C<N>::f() {}
```

使用泛型时也可能发生 C3855：

```cpp
// C3855c.cpp
// compile with: /clr
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GC1<T>::GC2 { };   // C3855
```

可能的解决方法：

```cpp
// C3855d.cpp
// compile with: /clr /c
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
ref struct GC1<T>::GC2 { };
```
