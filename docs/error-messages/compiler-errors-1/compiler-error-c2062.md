---
title: 编译器错误 C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: dcfac9629a90b82744f87ec105c30301b2102cdf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408740"
---
# <a name="compiler-error-c2062"></a>编译器错误 C2062

类型 type 意外

编译器不需要类型名称。

下面的示例生成 C2062:

```
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

C2062 也可能是因为编译器的方式在构造函数的参数列表中的句柄未定义的类型。 如果编译器遇到了未定义的 （拼写错误？） 类型，则假定该构造函数是一个表达式，并发出 C2062。 若要解决，只能在构造函数参数列表中使用定义的类型。