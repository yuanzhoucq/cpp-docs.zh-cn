---
title: "本机 C++ 中的事件处理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件处理, Visual C++"
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 本机 C++ 中的事件处理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在处理本机 C \+\+ 事件时，您分别使用 [event\_source](../windows/event-source.md) 和 [event\_receiver](../windows/event-receiver.md) 特性设置事件源和事件接收器，并指定 `type`\=`native`。  这些特性允许应用它们的类在本机的非 COM 上下文中激发和处理事件。  
  
## 声明事件  
 在事件源类中，对一个方法声明使用 [\_\_event](../cpp/event.md)关键字可将该方法声明为事件。  请确保声明该方法，但不要定义它；这样做会产生编译器错误，因为将该方法转换为事件时编译器会隐式定义它。  本机事件可以是带有零个或多个参数的方法。  返回类型可以是 void 或任何整型。  
  
## 定义事件处理程序  
 在事件接收器类中，可定义事件处理程序，这些处理程序是具有与它们将处理的事件匹配的签名（返回类型、调用约定和参数）的方法。  
  
## 将事件处理程序挂钩到事件  
 同样在事件接收器类中，可使用内部函数 [\_\_hook](../cpp/hook.md) 将事件与事件处理程序关联，并可使用 [\_\_unhook](../cpp/unhook.md) 取消事件与事件处理程序的关联。  您可将多个事件挂钩到一个事件处理程序，或将多个事件处理程序挂钩到一个事件。  
  
## 激发事件  
 若要激发事件，只需调用声明为事件源类中的事件的方法即可。  如果处理程序已挂钩到事件，则将调用处理程序。  
  
### 本机 C\+\+ 事件代码  
 以下示例演示如何在本机 C\+\+ 中激发事件。  若要编译并运行此示例，请参考代码中的注释。  
  
## 示例  
  
### 代码  
  
```  
// evh_native.cpp  
#include <stdio.h>  
  
[event_source(native)]  
class CSource {  
public:  
   __event void MyEvent(int nValue);  
};  
  
[event_receiver(native)]  
class CReceiver {  
public:  
   void MyHandler1(int nValue) {  
      printf_s("MyHandler1 was called with value %d.\n", nValue);  
   }  
  
   void MyHandler2(int nValue) {  
      printf_s("MyHandler2 was called with value %d.\n", nValue);  
   }  
  
   void hookEvent(CSource* pSource) {  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
  
   void unhookEvent(CSource* pSource) {  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
};  
  
int main() {  
   CSource source;  
   CReceiver receiver;  
  
   receiver.hookEvent(&source);  
   __raise source.MyEvent(123);  
   receiver.unhookEvent(&source);  
}  
```  
  
### Output  
  
```  
MyHandler2 was called with value 123.  
MyHandler1 was called with value 123.  
```  
  
## 请参阅  
 [事件处理](../cpp/event-handling.md)