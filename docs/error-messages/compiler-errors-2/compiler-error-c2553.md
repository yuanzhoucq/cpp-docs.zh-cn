---
title: 编译器错误 C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: aa3e97d576e994878ab5b080363c4c09b79f42ed
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756781"
---
# <a name="compiler-error-c2553"></a>编译器错误 C2553

"base_function"：重写虚函数返回类型与 "override_function" 不同

派生类中的函数尝试重写基类中的虚函数，但该派生类函数的返回类型与基类函数的返回类型不同。  重写函数签名必须与被重写的函数的签名匹配。

下面的示例生成 C2553：

```cpp
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
