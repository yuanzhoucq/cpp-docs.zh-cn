---
title: "编译器警告（等级 1）C4803 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4803"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4803"
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4803
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“method”: 引发方法的存储类与事件“event”的存储类不同  
  
 事件方法必须与事件声明具有相同的存储类。  编译器调整事件的方法以便使存储类相同。  
  
 如果有从接口实现事件的类，则会出现此警告。  编译器不为接口中的事件隐式生成引发方法。  当您在类中实现该接口时，编译器隐式生成引发方法，它不是虚方法，因此会出现警告。  
  
 有关如何关闭警告的信息，请参见 [warning](../../preprocessor/warning.md) 杂注。  
  
## 示例  
 可使用 **\/clr** 生成 C4803。  有关使用事件的更多信息，请参见 [event](../../windows/event-cpp-component-extensions.md)。  
  
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
  
## 示例  
 可使用 **\/clr:oldSyntax** 生成 C4803。  下面的示例生成 C4803。  
  
```  
// C4803_b.cpp  
// compile with: /clr:oldSyntax /W1  
using namespace System;  
  
public __delegate void Del();  
  
__gc struct E {  
   Del* _pd1;  
   virtual __event void add_E1(Del* pd1) {  
      _pd1 = dynamic_cast<Del*> (Delegate::Combine(_pd1, pd1));  
   }  
  
   virtual __event void remove_E1(Del* pd1) {  
      _pd1 = dynamic_cast<Del*> (Delegate::Remove(_pd1, pd1));  
   }  
  
   __event void raise_E1 () {   // C4803, add virtual  
      if (_pd1)  
         _pd1->Invoke();  
   }  
  
   void func() {  
      Console::WriteLine("In E::func()");  
   }  
};  
  
int main() {  
   E* ep = new E;  
   ep->E1 += new Del(ep, &E::func);  
   ep->E1();  
   ep->E1 -= new Del(ep, &E::func);  
   ep->E1();  
}  
```