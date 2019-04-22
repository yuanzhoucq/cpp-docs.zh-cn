---
title: __hook
ms.date: 11/04/2016
f1_keywords:
- __hook_cpp
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
ms.openlocfilehash: c4887d85e01344c171fb0fdfe957f2d8a669ff6a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58771664"
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

### <a name="parameters"></a>参数

*&SourceClass::EventMethod*<br/>
指向要将事件处理程序方法挂钩到的事件方法的指针：

- 本机C++事件：*SourceClass*是事件源类和*EventMethod*是事件。

- COM 事件：*SourceClass*是事件源接口和*EventMethod*是其方法之一。

- 托管的事件：*SourceClass*是事件源类和*EventMethod*是事件。

*interface*<br/>
要挂钩到的接口名*接收方*，仅适用于在其中 COM 事件接收器*layout_dependent*参数[event_receiver](../windows/attributes/event-receiver.md)属性是 **，则返回 true**。

*source*<br/>
指向事件源的实例的指针。 根据代码`type`中指定`event_receiver`，*源*可以是以下之一：

- 本机事件源对象指针。

- `IUnknown`-基于指针 （COM 源）。

- 托管对象指针（针对托管事件）。

*&ReceiverClass::HandlerMethod*<br/>
指向要挂钩到事件的事件处理程序方法的指针。 作为方法的类或引用相同，则为指定的处理程序如果未指定类名 **__hook**假定该类是在其中进行调用。

- 本机C++事件：*ReceiverClass*是事件接收器类和`HandlerMethod`是处理程序。

- COM 事件：*ReceiverClass*是事件接收器接口和`HandlerMethod`是其处理程序之一。

- 托管的事件：*ReceiverClass*是事件接收器类和`HandlerMethod`是处理程序。

*receiver*<br/>
（可选）指向事件接收器类的实例的指针。 如果未指定接收方，默认值是接收方类或结构中其 **__hook**调用。

## <a name="usage"></a>用法

可以在事件接收器类的外部的任何函数范围（包括 main）中使用。

## <a name="remarks"></a>备注

使用内部函数 **__hook**事件接收器关联或挂钩与事件方法的处理程序方法中。 随后会在源引发指定事件时调用指定的事件处理程序。 可以将多个处理程序挂钩到单个事件，或将多个事件挂钩到单个处理程序。

有两种形式的 **__hook**。 适用于 COM 事件接收器中，使用具体而言，在大多数情况下，第一种 （四个参数） 形式*layout_dependent*的参数[event_receiver](../windows/attributes/event-receiver.md)属性是**false**.

在这些情况下，当在其中一个方法上激发事件前，不需要在接口中挂钩所有方法；只需挂钩处理事件的方法。 可以使用的第二个 （两个参数） 窗体 **__hook**仅对在其中的 COM 事件接收器*layout_dependent* **= true**。

**__hook**返回一个长整型值。 非零返回值表示发生了错误（托管事件引发了异常）。

编译器将检查是否存在事件以及事件签名是否与委托签名一致。

除 COM 事件 **__hook**并 **__unhook**外部事件接收器可以调用。

使用的替代方法 **__hook**是使用 + = 运算符。

有关新语法中编码托管的事件的信息，请参阅[事件](../extensions/event-cpp-component-extensions.md)。

> [!NOTE]
> 模板类或结构不能包含事件。

## <a name="example"></a>示例

请参阅[本机 C++ 中的事件处理](../cpp/event-handling-in-native-cpp.md)和[COM 中的事件处理](../cpp/event-handling-in-com.md)示例。

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[事件处理](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
