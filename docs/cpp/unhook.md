---
title: __unhook |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unhook
- __unhook_cpp
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b95ff49c9b1f088ac38ffb0791f18f249b211e72
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="unhook"></a>__unhook
取消处理程序方法与事件的关联。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 **&** *SourceClass* `::` *EventMethod*  
 指向从中解除挂钩事件处理程序方法的事件方法的指针：  
  
-   本机 C++ 事件： *SourceClass*是事件源类和*EventMethod*是事件。  
  
-   COM 事件： *SourceClass*是事件源接口和*EventMethod*是其方法之一。  
  
-   托管事件： *SourceClass*是事件源类和*EventMethod*是事件。  
  
 `interface`  
 从解除挂钩的接口名称`receiver`，仅适用于在其中的 COM 事件接收器*layout_dependent*参数[event_receiver](../windows/event-receiver.md)属性是**true**.  
  
 *源*  
 指向事件源的实例的指针。 根据代码`type`中指定**event_receiver**，*源*可以是以下之一：  
  
-   本机事件源对象指针。  
  
-   **IUnknown**-基于指针 （COM 源）。  
  
-   托管对象指针（针对托管事件）。  
  
 **&** *ReceiverClass* `::` `HandlerMethod`  
 指向要从事件中解除挂钩的事件处理程序方法的指针。 处理程序将指定为类的方法或对同一方法的引用；如果不指定类名称，则 `__unhook` 假定该类是从中调用它的类。  
  
-   本机 C++ 事件： *ReceiverClass*是事件接收器类和`HandlerMethod`是处理程序。  
  
-   COM 事件： *ReceiverClass*是事件接收器接口和`HandlerMethod`是其处理程序之一。  
  
-   托管事件： *ReceiverClass*是事件接收器类和`HandlerMethod`是处理程序。  
  
 `receiver`（可选）  
 指向事件接收器类的实例的指针。 如果不指定接收器，则默认为在其中调用 `__unhook` 的接收器类或结构。  
  
## <a name="usage"></a>用法  
 可以在事件接收器类的外部的任何函数范围（包括 main）中使用。  
  
## <a name="remarks"></a>备注  
 使用事件接收器中的内部函数 `__unhook` 取消处理程序方法与事件方法的关联或从事件方法“解除挂钩”处理程序方法。  
  
 `__unhook` 有三种形式。 在大多数情况下，可以使用第一种 (four-argument) 形式。 只能为 COM 事件接收器使用 `__unhook` 的第二种 (two-argument) 形式；这将解除挂钩整个事件接口。 可以使用第三种 (one-argument) 形式从指定的源中解除挂钩所有委托。  
  
 非零返回值指示已发生错误（托管事件将引发异常）。  
  
 如果对尚未挂钩的事件和事件处理程序调用 `__unhook`，它将不起作用。  
  
 在编译时，编译器将验证事件是否存在，并利用指定的处理程序执行参数类型检查。  
  
 除 COM 事件外，可以在事件接收器的外部调用 `__hook` 和 `__unhook`。  
  
 作为使用 `__unhook` 的替代方式，可以使用 -= 运算符。  
  
 有关编码的新语法中的托管的事件的信息，请参阅[事件](../windows/event-cpp-component-extensions.md)。  
  
> [!NOTE]
>  模板类或结构不能包含事件。  
  
## <a name="example"></a>示例  
 请参阅[本机 C++ 中的事件处理](../cpp/event-handling-in-native-cpp.md)和[COM 中的事件处理](../cpp/event-handling-in-com.md)示例。  
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [event_source](../windows/event-source.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__raise](../cpp/raise.md)