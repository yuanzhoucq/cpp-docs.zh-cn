---
title: 编译器错误 C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: 7dd47ffbd9481f69f3799a94a17a53ccdffb2a84
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745013"
---
# <a name="compiler-error-c2391"></a>编译器错误 C2391

"identifier"： "friend" 不能在类型定义过程中使用

`friend` 声明包含完整的类声明。 `friend` 声明可以指定成员函数或详细的类型说明符，但不能指定完整的类声明。

下面的示例生成 C2326:

```cpp
// C2391.cpp
// compile with: /c
class D {
   void func( int );
};

class A {
   friend class B { int i; };   // C2391

   // OK
   friend class C;
   friend void D::func(int);
};
```
