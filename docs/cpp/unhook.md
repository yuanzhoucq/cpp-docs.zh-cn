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
ms.openlocfilehash: 84df5ad0ff27e6b09134b0f92f14f8e9b6fdc817
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233569"
---
# <a name="__unhook"></a>__unhook

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

**&***SourceClass* `::`*EventMethod*指向事件方法的指针，将从该事件方法解除挂钩事件处理程序方法：

- 本机 c + + 事件： *SourceClass*是事件源类， *EventMethod*是事件。

- COM 事件： *SourceClass*是事件源接口， *EventMethod*是其方法之一。

- 托管事件： *SourceClass*是事件源类， *EventMethod*是事件。

*interface*<br/>
要从*接收方*解除挂钩的接口名称，仅适用于 COM 事件接收器，其中[event_receiver](../windows/attributes/event-receiver.md)属性的*layout_dependent*参数是 **`true`** 。

*source*<br/>
指向事件源的实例的指针。 根据 `type` 中指定的代码 `event_receiver` ， *source*可以是以下项之一：

- 本机事件源对象指针。

- `IUnknown`基于的指针（COM 源）。

- 托管对象指针（针对托管事件）。

**&***ReceiverClass* `::`指向要 `HandlerMethod` 从事件中解除挂钩的事件处理程序方法的指针。 处理程序被指定为类的方法或对相同的引用;如果未指定类名，则 **`__unhook`** 假定类是在其中调用的类。

- 本机 c + + 事件： *ReceiverClass*是事件接收器类， `HandlerMethod` 是处理程序。

- COM 事件： *ReceiverClass*是事件接收器接口， `HandlerMethod` 它是其处理程序之一。

- 托管事件： *ReceiverClass*是事件接收器类， `HandlerMethod` 是处理程序。

*接收方*（可选）指向事件接收器类的实例的指针。 如果未指定接收方，则默认值为在其中调用的接收方类或结构 **`__unhook`** 。

## <a name="usage"></a>使用情况

可以在事件接收器类的外部的任何函数范围（包括 main）中使用。

## <a name="remarks"></a>备注

使用 **`__unhook`** 事件接收器中的内部函数将处理程序方法与事件方法取消关联。

有三种形式的 **`__unhook`** 。 在大多数情况下，可以使用第一种 (four-argument) 形式。 只能对 COM 事件接收器使用第二个（两个参数）形式 **`__unhook`** ; 这会解除整个事件接口的挂钩。 可以使用第三种 (one-argument) 形式从指定的源中解除挂钩所有委托。

非零返回值指示已发生错误（托管事件将引发异常）。

如果对 **`__unhook`** 尚未挂钩的事件和事件处理程序调用，它将不起作用。

在编译时，编译器将验证事件是否存在，并利用指定的处理程序执行参数类型检查。

除了 COM 事件 **`__hook`** 之外，还可以在 **`__unhook`** 事件接收器之外调用。

使用的替代方法 **`__unhook`** 是使用-= 运算符。

有关新语法中的托管事件编码的信息，请参阅[事件](../extensions/event-cpp-component-extensions.md)。

> [!NOTE]
> 模板类或结构不能包含事件。

## <a name="example"></a>示例

有关示例，请参阅[本机 c + + 中的事件处理](../cpp/event-handling-in-native-cpp.md)和[COM 中的事件处理](../cpp/event-handling-in-com.md)。

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
