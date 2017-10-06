---
title: "__hook |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __hook
dev_langs:
- C++
helpviewer_keywords:
- __hook keyword [C++]
- event handlers, connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 21bb75853d8664ad46bc48fc907946ae5a147f9a
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="hook"></a>__hook
将处理程序方法与事件关联。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 **&***SourceClass* `::` *EventMethod*  
 指向要将事件处理程序方法挂钩到的事件方法的指针：  
  
-   本机 c + + 事件： *SourceClass*是事件源类和*EventMethod*是事件。  
  
-   COM 事件： *SourceClass*是事件源接口和*EventMethod*是其方法之一。  
  
-   托管事件： *SourceClass*是事件源类和*EventMethod*是事件。  
  
 `interface`  
 要挂钩到的接口名称`receiver`，仅适用于在其中的 COM 事件接收器*layout_dependent*参数[event_receiver](../windows/event-receiver.md)属性是**true**.  
  
 *源*  
 指向事件源的实例的指针。 根据代码`type`中指定**event_receiver**，*源*可以是以下之一：  
  
-   本机事件源对象指针。  
  
-   **IUnknown**-基于指针 （COM 源）。  
  
-   托管对象指针（针对托管事件）。  
  
 **&***ReceiverClass* `::``HandlerMethod`  
 指向要挂钩到事件的事件处理程序方法的指针。 处理程序将指定为类的方法或对同一方法的引用；如果不指定类名称，则 `__hook` 假定该类是从中调用它的类。  
  
-   本机 c + + 事件： *ReceiverClass*是事件接收器类和`HandlerMethod`是处理程序。  
  
-   COM 事件： *ReceiverClass*是事件接收器接口和`HandlerMethod`是其处理程序之一。  
  
-   托管事件： *ReceiverClass*是事件接收器类和`HandlerMethod`是处理程序。  
  
 `receiver`（可选）  
 指向事件接收器类的实例的指针。 如果不指定接收器，则默认为在其中调用 `__hook` 的接收器类或结构。  
  
## <a name="usage"></a>用法  
 可以在事件接收器类的外部的任何函数范围（包括 main）中使用。  
  
## <a name="remarks"></a>备注  
 请使用事件接收器中的内部函数 `__hook` 将处理程序方法与事件方法关联或挂钩。 随后会在源引发指定事件时调用指定的事件处理程序。 可以将多个处理程序挂钩到单个事件，或将多个事件挂钩到单个处理程序。  
  
 `__hook` 有两种形式。 适用于在其中的 COM 事件接收器，使用具体而言，在大多数情况下，第一种 （四个形参） 形式*layout_dependent*参数[event_receiver](../windows/event-receiver.md)属性是**false**.  
  
 在这些情况下，当在其中一个方法上激发事件前，不需要在接口中挂钩所有方法；只需挂钩处理事件的方法。 你可以使用的第二个 (two-argument) 形式`__hook`仅为 COM 事件接收器在其中*layout_dependent***= true**。  
  
 `__hook` 将返回一个长值。 非零返回值表示发生了错误（托管事件引发了异常）。  
  
 编译器将检查是否存在事件以及事件签名是否与委托签名一致。  
  
 除 COM 事件外，可以在事件接收器的外部调用 `__hook` 和 `__unhook`。  
  
 使用 `__hook` 的替代方法是使用 += 运算符。  
  
 有关编码的新语法中的托管的事件的信息，请参阅[事件](../windows/event-cpp-component-extensions.md)。  
  
> [!NOTE]
>  模板类或结构不能包含事件。  
  
## <a name="example"></a>示例  
 请参阅[本机 c + + 中的事件处理](../cpp/event-handling-in-native-cpp.md)和[COM 中的事件处理](../cpp/event-handling-in-com.md)示例。  
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [事件处理](../cpp/event-handling.md)   
 [event_source](../windows/event-source.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__unhook](../cpp/unhook.md)   
 [__raise](../cpp/raise.md)
