---
title: 编译器警告 （等级 1） C4803 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4803
dev_langs:
- C++
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c574b51fc13f9224d48495f8b591a56abdc74966
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4803"></a>编译器警告（等级 1）C4803
method： 引发方法具有不同的存储类，该事件，从 event  
  
事件方法必须具有与事件声明相同的存储类。 编译器调整事件的方法，以便对存储类相同。  
  
如果你有实现来自接口的事件的类，则会出现此警告。 编译器不隐式生成的事件引发方法在接口中。 当类中实现该接口时，编译器隐式生成引发方法，该方法将不会虚拟的因此该警告。 有关事件的详细信息，请参阅[事件](../../windows/event-cpp-component-extensions.md)。  
  
请参阅[警告](../../preprocessor/warning.md)如何关闭一条警告信息的杂注。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4803。  
  
```  
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
