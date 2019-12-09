---
title: 编译器错误 C3731
ms.date: 11/04/2016
f1_keywords:
- C3731
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
ms.openlocfilehash: 9acf80eec0d36db64fa070d691533e7085754ac0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752946"
---
# <a name="compiler-error-c3731"></a>编译器错误 C3731

不兼容的事件 "function1" 和处理程序 "function2";事件源和事件处理程序必须为同一类型

事件源和事件接收器必须具有相同的类型（例如 `native` 与 `com` 类型）。 若要修复此错误，请使事件源和事件处理程序的类型匹配。

下面的示例生成 C3731：

```cpp
// C3731.cpp
// compile with: /clr
#using <mscorlib.dll>
[event_source(native)]
struct A {
   __event void MyEvent();
};

[event_receiver(managed)]
// try the following line instead
// [event_receiver(native)]
struct B {
   void func();
   B(A a) {
      __hook(&A::MyEvent, &a, &B::func);   // C3731
   }
};

int main() {
}
```
