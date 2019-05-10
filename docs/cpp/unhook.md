---
title: __unhook
ms.date: 11/04/2016
f1_keywords:
- __unhook
- __unhook_cpp
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
ms.openlocfilehash: e8f42c35024995c026ae10fc7f0ab3db77d1e5dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312149"
---
# <a name="unhook"></a>__unhook

取消处理程序方法与事件的关联。

## <a name="syntax"></a>语法

```cpp
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

**&** *SourceClass* `::` *EventMethod*指向从中解除挂钩事件处理程序方法的事件方法的指针：

- 本机C++事件：*SourceClass*是事件源类和*EventMethod*是事件。

- COM 事件：*SourceClass*是事件源接口和*EventMethod*是其方法之一。

- 托管的事件：*SourceClass*是事件源类和*EventMethod*是事件。

*interface*<br/>
接口名称从解除挂钩*接收方*，仅适用于在其中 COM 事件接收器*layout_dependent*参数[event_receiver](../windows/attributes/event-receiver.md)特性是 **，则返回 true**。

*source*<br/>
指向事件源的实例的指针。 根据代码`type`中指定`event_receiver`，*源*可以是以下之一：

- 本机事件源对象指针。

- `IUnknown`-基于指针 （COM 源）。

- 托管对象指针（针对托管事件）。

**&** *ReceiverClass* `::` `HandlerMethod`指向要从事件中解除挂钩的事件处理程序方法的指针。 作为方法的类或引用相同，则为指定的处理程序如果未指定类名 **__unhook**假定该类是在其中进行调用。

- 本机C++事件：*ReceiverClass*是事件接收器类和`HandlerMethod`是处理程序。

- COM 事件：*ReceiverClass*是事件接收器接口和`HandlerMethod`是其处理程序之一。

- 托管的事件：*ReceiverClass*是事件接收器类和`HandlerMethod`是处理程序。

*接收方*（可选） 指向事件接收器类的实例的指针。 如果未指定接收方，默认值是接收方类或结构中其 **__unhook**调用。

## <a name="usage"></a>用法

可以在事件接收器类的外部的任何函数范围（包括 main）中使用。

## <a name="remarks"></a>备注

使用内部函数 **__unhook**事件接收器以取消关联或"解除挂钩"处理程序方法与事件方法中。

有三种形式 **__unhook**。 在大多数情况下，可以使用第一种 (four-argument) 形式。 可以使用的第二个 （两个参数） 窗体 **__unhook**仅为 COM 事件接收器; 这解除挂钩整个事件接口。 可以使用第三种 (one-argument) 形式从指定的源中解除挂钩所有委托。

非零返回值指示已发生错误（托管事件将引发异常）。

如果您调用 **__unhook**上的事件和尚未挂钩的事件处理程序，它不会产生影响。

在编译时，编译器将验证事件是否存在，并利用指定的处理程序执行参数类型检查。

除 COM 事件 **__hook**并 **__unhook**外部事件接收器可以调用。

使用的替代方法 **__unhook**是使用-= 运算符。

有关新语法中编码托管的事件的信息，请参阅[事件](../extensions/event-cpp-component-extensions.md)。

> [!NOTE]
>  模板类或结构不能包含事件。

## <a name="example"></a>示例

请参阅[本机 C++ 中的事件处理](../cpp/event-handling-in-native-cpp.md)和[COM 中的事件处理](../cpp/event-handling-in-com.md)示例。

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)