---
title: "__unhook | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__unhook"
  - "__unhook_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__unhook 关键字 [C++]"
  - "事件处理程序, 取消事件关联"
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# __unhook
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取消处理程序方法与事件的关联。  
  
## 语法  
  
```  
  
      long  __unhook(  
   &SourceClass::EventMethod,  
   source,  
   &ReceiverClass::HandlerMethod  
   [, receiver = this]   
);  
long  __unhook(   
   interface,  
   source  
);  
long  __unhook(  
   source   
);  
```  
  
#### 参数  
 **&** *SourceClass* `::` *EventMethod*  
 指向从中解除挂钩事件处理程序方法的事件方法的指针：  
  
-   本机 C\+\+ 事件：*SourceClass* 是事件源类，*EventMethod* 是事件。  
  
-   COM 事件：*SourceClass* 是事件源接口，*EventMethod* 是其方法之一。  
  
-   托管事件：*SourceClass* 是事件源类，*EventMethod* 是事件。  
  
 `interface`  
 将从 `receiver` 中解除挂钩的接口名称，仅适用于 COM 事件接收器，其中 [event\_receiver](../windows/event-receiver.md) 特性的 *layout\_dependent* 参数为 **true**。  
  
 *source*  
 指向事件源的实例的指针。  根据 **event\_receiver** 中指定的代码 `type`，*source* 可为下列项之一：  
  
-   本机事件源对象指针。  
  
-   基于 **IUnknown** 的指针（COM 源）。  
  
-   托管对象指针（针对托管事件）。  
  
 **&** *ReceiverClass* `::` `HandlerMethod`  
 指向要从事件中解除挂钩的事件处理程序方法的指针。  处理程序将指定为类的方法或对同一方法的引用；如果不指定类名称，则 `__unhook` 假定该类是从中调用它的类。  
  
-   本机 C\+\+ 事件：*ReceiverClass* 是事件接收器类，`HandlerMethod` 是处理程序。  
  
-   COM 事件：*ReceiverClass* 是事件接收器接口，`HandlerMethod` 是其处理程序之一。  
  
-   托管事件：*ReceiverClass* 是事件接收器类，`HandlerMethod` 是处理程序。  
  
 `receiver`（可选）  
 指向事件接收器类的实例的指针。  如果不指定接收器，则默认为在其中调用 `__unhook` 的接收器类或结构。  
  
## 用法  
 可以在事件接收器类的外部的任何函数范围（包括 main）中使用。  
  
## 备注  
 使用事件接收器中的内部函数 `__unhook` 取消处理程序方法与事件方法的关联或从事件方法“解除挂钩”处理程序方法。  
  
 `__unhook` 有三种形式。  在大多数情况下，可以使用第一种 \(four\-argument\) 形式。  只能为 COM 事件接收器使用 `__unhook` 的第二种 \(two\-argument\) 形式；这将解除挂钩整个事件接口。  可以使用第三种 \(one\-argument\) 形式从指定的源中解除挂钩所有委托。  
  
 非零返回值指示已发生错误（托管事件将引发异常）。  
  
 如果对尚未挂钩的事件和事件处理程序调用 `__unhook`，它将不起作用。  
  
 在编译时，编译器将验证事件是否存在，并利用指定的处理程序执行参数类型检查。  
  
 除 COM 事件外，可以在事件接收器的外部调用 `__hook` 和 `__unhook`。  
  
 作为使用 `__unhook` 的替代方式，可以使用 \-\= 运算符。  
  
 有关新语法中编码托管事件的信息，请参阅[event](../windows/event-cpp-component-extensions.md)。  
  
> [!NOTE]
>  模板类或结构不能包含事件。  
  
## 示例  
 有关示例，请参阅[本机 C\+\+ 中的事件处理](../cpp/event-handling-in-native-cpp.md)和 [COM 中的事件处理](../cpp/event-handling-in-com.md)。  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [event\_source](../windows/event-source.md)   
 [event\_receiver](../windows/event-receiver.md)   
 [\_\_event](../cpp/event.md)   
 [\_\_hook](../cpp/hook.md)   
 [\_\_raise](../cpp/raise.md)