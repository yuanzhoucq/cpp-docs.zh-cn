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
ms.openlocfilehash: 221ffc30a9b8a40c44f8009dfa511b72aa160e01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337554"
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

**&***SourceClass* `::` *eventMethod*指向从中取消挂钩的事件处理程序方法的指针：

- 本机C++事件：*源类*是事件源类，*事件方法*是事件。

- COM 事件 *：SourceClass*是事件源接口，*事件方法*是其方法之一。

- 托管事件：*源类*是事件源类，*事件方法*是事件。

*interface*<br/>
接口名称从接收器取消挂接 *，* 仅适用于[EVENT_RECEIVER属性](../windows/attributes/event-receiver.md)*的layout_dependent*参数为**true**的 COM 事件接收器。

*源*<br/>
指向事件源的实例的指针。 根据 中`event_receiver`指定的`type`代码 *，源代码*可以是以下代码之一：

- 本机事件源对象指针。

- 基于`IUnknown`指针 （COM 源）。

- 托管对象指针（针对托管事件）。

**&***接收器类*`::``HandlerMethod`A 指向事件处理程序方法的指针，以便从事件中取消挂接。 处理程序被指定为类的方法或对同一类的引用;如果不指定类名称 **，__unhook**假定该类是调用该类的类。

- 本机C++事件：*接收方类*是事件接收者类`HandlerMethod`，是处理程序。

- COM 事件：*接收器类*是事件接收器接口，`HandlerMethod`是其处理程序之一。

- 托管事件：*接收方类*是事件接收方类`HandlerMethod`，是处理程序。

*接收器*（可选）指向事件接收器类实例的指针。 如果不指定接收器，则默认值为调用 **__unhook**的接收器类或结构。

## <a name="usage"></a>使用情况

可以在事件接收器类的外部的任何函数范围（包括 main）中使用。

## <a name="remarks"></a>备注

使用事件接收器中的内在函数 **__unhook**将处理程序方法与事件方法分离或"取消挂钩"。

有三种 **__unhook**形式。 在大多数情况下，可以使用第一种 (four-argument) 形式。 只能对 COM 事件接收器使用第二种（两参数 **）__unhook**形式;这将取消挂接整个事件接口。 可以使用第三种 (one-argument) 形式从指定的源中解除挂钩所有委托。

非零返回值指示已发生错误（托管事件将引发异常）。

如果在尚未挂接的事件和事件处理程序上调用 **__unhook，** 它将不起作用。

在编译时，编译器将验证事件是否存在，并利用指定的处理程序执行参数类型检查。

除 COM 事件外 **，__hook**和 **__unhook**可以在事件接收器外部调用。

使用 **__unhook**的替代方法是使用 -# 运算符。

有关在新语法中编码托管事件的信息，请参阅[事件](../extensions/event-cpp-component-extensions.md)。

> [!NOTE]
> 模板类或结构不能包含事件。

## <a name="example"></a>示例

有关示例[，请参阅本机C++中的事件处理](../cpp/event-handling-in-native-cpp.md)和[COM 中的事件处理](../cpp/event-handling-in-com.md)。

## <a name="see-also"></a>另请参阅

[Keywords](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
