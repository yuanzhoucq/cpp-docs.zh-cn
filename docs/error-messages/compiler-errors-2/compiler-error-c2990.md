---
title: 编译器错误 C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: f7327b7d2b0cc9fa4b617a9a6033116c43db6258
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366324"
---
# <a name="compiler-error-c2990"></a>编译器错误 C2990

class： 非类类型已被声明为类类型

非泛型或模板类重新定义泛型或模板类。 检查冲突的标头文件。

下面的示例生成 C2990:

```
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

使用泛型时也可能导致 C2990:

```
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

由于在视觉对象中的重大更改也可能导致 C2990C++编译器为视觉对象C++2005;编译器现在需要为同一类型的多个声明是相对于模板规范相同。

下面的示例生成 C2990:

```
// C2990c.cpp
// compile with: /c
template<class T>
class A;

template<class T>
struct A2 {
   friend class A;   // C2990
};

// OK
template<class T>
struct B {
   template<class T>
   friend class A;
};
```