---
title: 编译器错误 C3739
ms.date: 11/04/2016
f1_keywords:
- C3739
helpviewer_keywords:
- C3739
ms.assetid: acffe894-08b8-4bf2-9249-9501e6e2bad3
ms.openlocfilehash: 48d0fef86908f3ba5a547417d0625febc5226454
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752699"
---
# <a name="compiler-error-c3739"></a>编译器错误 C3739

"class"：只有当 event_receiver 的 "layout_dependent" 参数为 true 时，才支持语法

您尝试挂钩整个事件接口，但是 `layout_dependent` [event_receiver](../../windows/event-receiver.md)属性不为 true;您必须一次挂钩一个事件。

下面的示例生成 C3739：

```cpp
// C3739.cpp
struct A
{
   __event void e();
};

// event_receiver is implied
// [ event_receiver(layout_dependent=false)]

// use the following line instead
// [event_receiver(com, layout_dependent=true), coclass ]
struct B
{
   void f();
   B(A* a)
   {
      __hook(A, a, &B::f);   // C3739
      // use the following line instead to hook a single event
      // __hook(&A::e, a, &B::f);
   }
};

int main()
{
}
```
