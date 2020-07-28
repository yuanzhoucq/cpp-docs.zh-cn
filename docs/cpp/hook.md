---
title: __hook
ms.date: 11/04/2016
f1_keywords:
- __hook_cpp
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
ms.openlocfilehash: 5a0eaf0a3bc0617dbcd1f43805af8a95291e7e47
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188162"
---
# <a name="__hook"></a>__hook

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

*&SourceClass：： EventMethod*<br/>
指向要将事件处理程序方法挂钩到的事件方法的指针：

- 本机 c + + 事件： *SourceClass*是事件源类， *EventMethod*是事件。

- COM 事件： *SourceClass*是事件源接口， *EventMethod*是其方法之一。

- 托管事件： *SourceClass*是事件源类， *EventMethod*是事件。

*interface*<br/>
与*接收方*挂钩的接口名称，仅适用于 COM 事件接收器，其中[event_receiver](../windows/attributes/event-receiver.md)属性的*layout_dependent*参数是 **`true`** 。

*source*<br/>
指向事件源的实例的指针。 根据 `type` 中指定的代码 `event_receiver` ， *source*可以是以下项之一：

- 本机事件源对象指针。

- `IUnknown`基于的指针（COM 源）。

- 托管对象指针（针对托管事件）。

*&ReceiverClass：： HandlerMethod*<br/>
指向要挂钩到事件的事件处理程序方法的指针。 处理程序被指定为类的方法或对相同的引用;如果未指定类名，则 **`__hook`** 假定类是在其中调用的类。

- 本机 c + + 事件： *ReceiverClass*是事件接收器类， `HandlerMethod` 是处理程序。

- COM 事件： *ReceiverClass*是事件接收器接口， `HandlerMethod` 它是其处理程序之一。

- 托管事件： *ReceiverClass*是事件接收器类， `HandlerMethod` 是处理程序。

*端*<br/>
可有可无指向事件接收器类的实例的指针。 如果未指定接收方，则默认值为在其中调用的接收方类或结构 **`__hook`** 。

## <a name="usage"></a>使用情况

可以在事件接收器类的外部的任何函数范围（包括 main）中使用。

## <a name="remarks"></a>备注

使用事件接收器中的内部函数将 **`__hook`** 处理程序方法与事件方法关联或挂钩。 随后会在源引发指定事件时调用指定的事件处理程序。 可以将多个处理程序挂钩到单个事件，或将多个事件挂钩到单个处理程序。

有两种形式的 **`__hook`** 。 在大多数情况下，你可以使用第一种（四参数）形式，具体而言，就是对于 COM 事件接收，其中[event_receiver](../windows/attributes/event-receiver.md)属性的*layout_dependent*参数是 **`false`** 。

在这些情况下，当在其中一个方法上激发事件前，不需要在接口中挂钩所有方法；只需挂钩处理事件的方法。 只能 **`__hook`** 对*layout_dependent*为**true**的 COM 事件接收器使用第二个（两个参数）形式。

**`__hook`** 返回一个长整型值。 非零返回值表示发生了错误（托管事件引发了异常）。

编译器将检查是否存在事件以及事件签名是否与委托签名一致。

除了 COM 事件 **`__hook`** 之外，还可以在 **`__unhook`** 事件接收器之外调用。

使用的替代方法 **`__hook`** 是使用 + = 运算符。

有关新语法中的托管事件编码的信息，请参阅[事件](../extensions/event-cpp-component-extensions.md)。

> [!NOTE]
> 模板类或结构不能包含事件。

## <a name="example"></a>示例

有关示例，请参阅[本机 c + + 中的事件处理](../cpp/event-handling-in-native-cpp.md)和[COM 中的事件处理](../cpp/event-handling-in-com.md)。

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[事件处理](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
