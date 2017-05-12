---
title: "事件 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31c8e08a-00ad-40f9-8f7e-124864aaad58
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 17
---
# 事件 (C++/CX)
[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型可声明（即发布）事件，同一组件或其他组件中的客户端代码可通过将调用事件处理程序的方法与事件相关联来订阅这些事件。 一个事件可以有多个事件处理程序与之关联。 当发布对象引发事件时，将调用所有事件处理程序。 这样，订阅类可在发布者引发事件时执行任何适当的自定义操作。 属于委托类型的事件可指定在所有事件处理程序订阅事件时所需的签名。  
  
## 使用 Windows 组件中的事件  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]中的许多组件均公开了事件。 例如，当传感器报告新的发光值时，LightSensor 对象触发 ReadingChanged 事件。 在程序中使用 LightSensor 对象时，可定义一个在激发 ReadingChanged 事件时调用的方法。 该方法可执行你希望的任意功能；唯一的要求是其签名必须与委托的签名匹配。有关如何创建委托事件处理程序和订阅事件的更多信息，请参见[委托](../cppcx/delegates-c-cx.md)。  
  
## 创建自定义事件  
  
### 声明  
 你可以在 ref 类或接口中声明事件，它可具有公共、内部（公共\/私有）、公共受保护、受保护、私有受保护或私有可访问性。 在声明事件时，编译器会在内部创建一个对象，该对象将公开两个方法：add 和 remove。 在订阅对象寄存器事件处理程序时，事件对象会将其存储在集合中。 激发事件时，事件对象将依次调用其列表中的所有处理程序。 普通事件（如以下示例中的事件）具有隐式后备存储，以及隐式的 `add` 和 `remove` 访问器方法。 你可以按照对属性指定自定义 `get` 和 `set` 访问器的方式指定自己的访问器。  实现类不能手动遍历常用事件中的事件订阅服务器列表。  
  
 下面的示例演示如何声明和触发事件。 请注意，该事件有一个委托类型并用“^”符号声明。  
  
 [!code-cpp[cx_events#01](../snippets/cpp/VS_Snippets_Misc/cx_events/cpp/cx_events/class1.h#01)]  
  
### 用法  
 下面的示例演示订阅类如何使用 `+=` 运算符订阅事件并在激发事件时调用事件处理程序。 请注意，提供的函数与 `EventTest` 命名空间中的发布程序端上定义的委托的签名匹配。  
  
 [!code-cpp[cx_events#02](../snippets/cpp/VS_Snippets_Misc/cx_events/cpp/eventsupportinvs/eventclientclass.h#02)]  
  
> [!WARNING]
>  通常，除非要格外注意以避免循环引用，否则更好的做法是对事件处理程序使用命名函数而不是 lambda。 命名函数会通过弱引用捕获“this”指针，而 lambda 通过强引用捕获该指针并创建一个循环引用。 有关更多信息，请参见[弱引用和中断循环 \(C\+\+\/CX\)](../cppcx/weak-references-and-breaking-cycles-c-cx.md)。  
  
### 自定义添加和移除方法  
 在内部，事件具有添加方法、移除方法和引发方法。 在客户端代码订阅事件时，将调用添加方法，并且传入的委托将添加到事件的调用列表中。 发布类调用事件，这将导致调用 raise\(\) 方法，并依次调用列表中的每个委托。 订阅方可将其自身从委托列表中移除，这将导致调用事件的移除方法。 如果你未在代码中定义这些方法，则编译器将提供这些方法的默认版本；它们称为常用事件。 在许多情况下，只需一个常用事件。  
  
 如果你必须执行自定义逻辑以响应添加或移除订户的操作，则可以为事件指定自定义添加、移除和引发方法。 例如，如果你具有只在报告事件时才需要的高开销对象，那么你可以延迟创建该对象，直到客户端实际订阅事件时为止。  
  
 下一个示例演示如何在事件中添加自定义添加、移除和引发方法：  
  
 [!code-cpp[cx_events#03](../snippets/cpp/VS_Snippets_Misc/cx_events/cpp/cx_events/class1.h#03)]  
  
## 从订户端移除事件处理程序  
 在某些少见的情况下，你可能希望移除先前订阅的事件的事件处理程序。 例如，你可能要用另一个事件处理程序替换它，或者删除它占有的一些资源。 若要移除处理程序，必须存储自 `+=` 操作返回的 EventRegistrationToken。 然后，可以对标记使用 `-=` 运算符以移除事件处理程序。  但是，即使在移除原始处理程序后，也仍可以调用它。 因此，如果你希望移除事件处理程序，则在移除事件后创建一个成员标志并设置它，然后在事件处理程序中检查该标志，如果已设置，则立即返回。 下一个示例演示基本模式。  
  
 [!code-cpp[cx_events#04](../snippets/cpp/VS_Snippets_Misc/cx_events/cpp/eventsupportinvs/eventclientclass.h#04)]  
  
## 备注  
 多个处理程序可以与同一事件关联。 事件源按顺序从同一线程调用到所有事件处理程序。 如果一个事件接收器在事件处理程序方法内受阻，则它将阻止事件源为该事件调用其他事件处理程序。  
  
 事件源对事件接收器调用事件处理程序的顺序不能保证，可能因调用而异。  
  
## 请参阅  
 [类型系统](../cppcx/type-system-c-cx.md)   
 [委托](../cppcx/delegates-c-cx.md)   
 [Visual C\+\+ 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)