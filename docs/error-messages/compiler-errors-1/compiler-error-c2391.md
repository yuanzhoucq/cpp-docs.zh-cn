---
title: 编译器错误 C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: f000287c5934a39d56342bce0f6c9ca2c69e2297
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212730"
---
# <a name="compiler-error-c2391"></a>编译器错误 C2391

"identifier"： "friend" 不能在类型定义过程中使用

**`friend`** 声明包含完整的类声明。 **`friend`** 声明可以指定成员函数或详细的类型说明符，但不能指定完整的类声明。

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
