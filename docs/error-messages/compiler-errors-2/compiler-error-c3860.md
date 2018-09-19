---
title: 编译器错误 C3860 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3860
dev_langs:
- C++
helpviewer_keywords:
- C3860
ms.assetid: 1fb5110d-594e-4f1c-8773-888233af1313
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4727a910427ecd23b5f699fc15bdcdc48a51f687
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073668"
---
# <a name="compiler-error-c3860"></a>编译器错误 C3860

类类型名称后面的类型实参列表必须列出使用类型参数列表中的顺序中的参数

泛型或模板的参数列表的格式不正确。

下面的示例生成 C3860:

```
// C3860.cpp
// compile with: /LD
template <class T1, class T2>
struct A {
   void f();
};

template <class T2, class T1>
void A<T1, T2>::f() {}   // C3860
```

可能的解决方法：

```
// C3860b.cpp
// compile with: /c
template <class T1, class T2>
struct A {
   void f();
};

template <class T2, class T1>
void A<T2, T1>::f() {}
```

使用泛型时，也可能发生 C3860:

```
// C3860c.cpp
// compile with: /clr
generic<class T,class U>
ref struct GC {
   void f();
};

generic<class T, class U>
void GC<T,T>::f() {}   // C3860
```

可能的解决方法：

```
// C3860d.cpp
// compile with: /clr /c
generic<class T,class U>
ref struct GC {
   void f();
};

generic<class T, class U>
void GC<T,U>::f() {}
```