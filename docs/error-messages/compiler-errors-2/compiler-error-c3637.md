---
title: 编译器错误 C3637 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3637
dev_langs:
- C++
helpviewer_keywords:
- C3637
ms.assetid: 72391377-8519-43d9-870a-73a6423deb74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 958ffc0d3aab641859b13570a94b159de80f2c7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117449"
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