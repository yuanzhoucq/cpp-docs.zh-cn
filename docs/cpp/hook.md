---
title: "__hook | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__hook_cpp"
  - "__hook"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__hook 关键字 [C++]"
  - "事件处理程序, 将事件连接到"
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# __hook
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将处理程序方法与事件关联。  
  
## 语法  
  
```  
  
      long __hook(  
   &SourceClass::EventMethod,  
   source,  
   &ReceiverClass::HandlerMethod  
   [, receiver = this]  
);  
long __hook(  
   interface,  
   source  
);  
```  
  
#### 参数  
 **&** *SourceClass* `::` *EventMethod*  
 指向要将事件处理程序方法挂钩到的事件方法的指针：  
  
-   本机 C\+\+ 事件：*SourceClass* 是事件源类，*EventMethod* 是事件。  
  
-   COM 事件：*SourceClass* 是事件源接口，*EventMethod* 是其方法之一。  
  
-   托管事件：*SourceClass* 是事件源类，*EventMethod* 是事件。  
  
 `interface`  
 要挂钩到 `receiver` 的接口名称，仅适用于 COM 事件接收器，其中 [event\_receiver](../windows/event-receiver.md) 特性的 *layout\_dependent* 参数为 **true**。  
  
 *source*  
 指向事件源的实例的指针。  根据 **event\_receiver** 中指定的代码 `type`，*source* 可为下列项之一：  
  
-   本机事件源对象指针。  
  
-   基于 **IUnknown** 的指针（COM 源）。  
  
-   托管对象指针（针对托管事件）。  
  
 **&** *ReceiverClass* `::` `HandlerMethod`  
 指向要挂钩到事件的事件处理程序方法的指针。  处理程序将指定为类的方法或对同一方法的引用；如果不指定类名称，则 `__hook` 假定该类是从中调用它的类。  
  
-   本机 C\+\+ 事件：*ReceiverClass* 是事件接收器类，`HandlerMethod` 是处理程序。  
  
-   COM 事件：*ReceiverClass* 是事件接收器接口，`HandlerMethod` 是其处理程序之一。  
  
-   托管事件：*ReceiverClass* 是事件接收器类，`HandlerMethod` 是处理程序。  
  
 `receiver`（可选）  
 指向事件接收器类的实例的指针。  如果不指定接收器，则默认为在其中调用 `__hook` 的接收器类或结构。  
  
## 用法  
 可以在事件接收器类的外部的任何函数范围（包括 main）中使用。  
  
## 备注  
 请使用事件接收器中的内部函数 `__hook` 将处理程序方法与事件方法关联或挂钩。  随后会在源引发指定事件时调用指定的事件处理程序。  可以将多个处理程序挂钩到单个事件，或将多个事件挂钩到单个处理程序。  
  
 `__hook` 有两种形式。  大多数情况下，可以使用第一种（四个形参）形式，具体而言，就是针对其中的 [event\_receiver](../windows/event-receiver.md) 特性的 *layout\_dependent* 参数是 **false** 的 COM 事件接收器。  
  
 在这些情况下，当在其中一个方法上激发事件前，不需要在接口中挂钩所有方法；只需挂钩处理事件的方法。  可以只对 *layout\_dependent***\=true** 的 COM 事件接收器使用第二种（二个形参）形式的 `__hook`。  
  
 `__hook` 将返回一个长值。  非零返回值表示发生了错误（托管事件引发了异常）。  
  
 编译器将检查是否存在事件以及事件签名是否与委托签名一致。  
  
 除 COM 事件外，可以在事件接收器的外部调用 `__hook` 和 `__unhook`。  
  
 使用 `__hook` 的替代方法是使用 \+\= 运算符。  
  
 有关新语法中编码托管事件的信息，请参阅[event](../windows/event-cpp-component-extensions.md)。  
  
> [!NOTE]
>  模板类或结构不能包含事件。  
  
## 示例  
 有关示例，请参阅[本机 C\+\+ 中的事件处理](../cpp/event-handling-in-native-cpp.md)和 [COM 中的事件处理](../cpp/event-handling-in-com.md)。  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [事件处理](../cpp/event-handling.md)   
 [event\_source](../windows/event-source.md)   
 [event\_receiver](../windows/event-receiver.md)   
 [\_\_unhook](../cpp/unhook.md)   
 [\_\_raise](../cpp/raise.md)