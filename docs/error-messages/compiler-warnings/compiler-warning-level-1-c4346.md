---
title: 编译器警告（等级 1）C4346
ms.date: 11/04/2016
f1_keywords:
- C4346
helpviewer_keywords:
- C4346
ms.assetid: 68ee562d-cca9-4a2a-9a1b-14ad1a1e7396
ms.openlocfilehash: 53381ca6e33321001299ce27bce550c5b2b8f59e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187213"
---
# <a name="compiler-warning-level-1-c4346"></a>编译器警告（等级 1）C4346

name： 依赖名称不是类型

[Typename](../../cpp/typename.md)关键字是必需的如果将依赖名称将被视为一种类型。 为视觉对象的所有版本的工作都方式相同的代码C++，添加`typename`到声明。

下面的示例生成 C4346:

```
// C4346.cpp
// compile with: /WX /LD
template<class T>
struct C {
   T::X* x;   // C4346
   // try the following line instead
   // typename T::X* x;
};
```

以下示例显示了其他示例其中**typename**是必需的关键字：

```
// C4346b.cpp
// compile with: /LD /W1
template<class T>
const typename T::X& f(typename T::Z* p);   // Required in both places

template<class T, int N>
struct L{};

template<class T>
struct M : public L<typename T::Type, T::Value>
{   // required on type argument, not on non-type argument
   typedef typename T::X   Type;
   Type f();   // OK: "Type" is a type-specifer
   typename T::X g();   // typename required
   operator typename T::Z();   // typename required
};
```

这样，

```
// C4346c.cpp
// compile with: /LD /WX
struct Y {
   typedef int Y_t;
};

template<class T>
struct A {
   typedef Y A_t;
};

template<class T>
struct B {
   typedef /*typename*/ A<T>::A_t B_t;   // C4346 typename needed here
   typedef /*typename*/ B_t::Y_t  B_t2;   // typename also needed here
};
```