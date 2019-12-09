---
title: 编译器错误 C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: 1c58c2d5da0049ec670e11c930b397caec3cbbee
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751516"
---
# <a name="compiler-error-c2990"></a>编译器错误 C2990

"class"：非类类型已声明为类类型

非泛型或模板类重新定义泛型或模板类。 检查标头文件中的冲突。

下面的示例生成 C2990：

```cpp
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

使用泛型时也可能发生 C2990：

```cpp
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

由于 Microsoft C++编译器 For Visual Studio 2005 中的重大更改，也可能会发生 C2990;编译器现在要求同类型的多个声明对于模板规范是相同的。

下面的示例生成 C2990：

```cpp
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
