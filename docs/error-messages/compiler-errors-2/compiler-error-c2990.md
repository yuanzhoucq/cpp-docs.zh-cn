---
title: 编译器错误 C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: 16c111a0fb8608615abaee495680fa38920b6c77
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447342"
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

C2990 也可能是因为在 microsoft 一项重大更改C++Visual Studio 2005; 编译器编译器现在需要为同一类型的多个声明是相对于模板规范相同。

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