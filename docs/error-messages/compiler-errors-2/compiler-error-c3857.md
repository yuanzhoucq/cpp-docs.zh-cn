---
title: 编译器错误 C3857
ms.date: 11/04/2016
f1_keywords:
- C3857
helpviewer_keywords:
- C3857
ms.assetid: 9f746d1e-9708-4945-bc29-3150d5371d3c
ms.openlocfilehash: 1270d09c870bfdf9f390d6afb1625ad3e99e01a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265433"
---
# <a name="compiler-error-c3857"></a>编译器错误 C3857

type： 不允许多个类型参数列表

为相同的类型，这不允许指定多个模板或泛型。

下面的示例生成 C3857:

```
// C3857.cpp
template <class T, class TT>
template <class T2>    // C3857
struct B {};
```

可能的解决方法：

```
// C3857b.cpp
// compile with: /c
template <class T, class TT, class T2>
struct B {};
```

使用泛型时，也可能发生 C3857:

```
// C3857c.cpp
// compile with: /clr
generic <typename T>
generic <typename U>
ref class GC;   // C3857
```

可能的解决方法：

```
// C3857d.cpp
// compile with: /clr /c
generic <typename U>
ref class GC;
```