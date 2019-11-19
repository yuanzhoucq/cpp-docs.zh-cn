---
title: 编译器警告（等级1） C4803
ms.date: 11/04/2016
f1_keywords:
- C4803
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
ms.openlocfilehash: ebf7b3baec3519a142c7a1835aa15a980974bb48
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052351"
---
# <a name="compiler-warning-level-1-c4803"></a>编译器警告（等级1） C4803

"method"： raise 方法的存储类与事件 "event" 的存储类不同

事件方法必须与事件声明具有相同的存储类。 编译器调整事件的方法，以便存储类相同。

如果某个类实现了接口中的事件，则会出现此警告。 编译器不会为接口中的事件隐式生成引发方法。 在类中实现该接口时，编译器会隐式生成一个 raise 方法，并且该方法将不是虚拟的，因此会出现警告。 有关事件的详细信息，请参阅[事件](../../extensions/event-cpp-component-extensions.md)。

有关如何关闭警告的信息，请参阅[警告](../../preprocessor/warning.md)杂注。

## <a name="example"></a>示例

下面的示例生成 C4803。

```cpp
// C4803.cpp
// compile with: /clr /W1
using namespace System;

public delegate void Del();

ref struct E {
   Del ^ _pd1;
   event Del ^ E1 {
      void add (Del ^ pd1) {
         _pd1 = dynamic_cast<Del ^>(Delegate::Combine(_pd1, pd1));
      }

      void remove(Del^ pd1) {
         _pd1 = dynamic_cast<Del^> (Delegate::Remove(_pd1, pd1));
      }

      virtual void raise() {   // C4803 warning (remove virtual)
         if (_pd1)
            _pd1();
      }
   }

   void func() {
      Console::WriteLine("In E::func()");
   }
};

int main() {
   E ^ ep = gcnew E;
   ep->E1 += gcnew Del(ep, &E::func);
   ep->E1();
   ep->E1 -= gcnew Del(ep, &E::func);
   ep->E1();
}
```
