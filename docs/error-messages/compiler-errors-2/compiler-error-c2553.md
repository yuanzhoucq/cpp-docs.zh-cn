---
title: 编译器错误 C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: 11cb2b83d958f0c59d05034a716a022f00b326ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353180"
---
# <a name="compiler-error-c2553"></a>编译器错误 C2553

base_function： 重写虚函数返回类型不同于 override_function

在派生类中的函数试图重写基类中的虚函数，但派生的类函数不具有相同的返回类型作为基类函数。  重写函数签名必须与被重写函数的签名匹配。

下面的示例生成 C2553:

```
// C2553.cpp
// compile with: /clr /c
ref struct C {
   virtual void f();
};

ref struct D : C {
   virtual int f() override ;   // C2553

   // try the following line instead
   // virtual void f() override;
};
```