---
title: event_receiver (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_receiver
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
ms.openlocfilehash: 81a3ec88c336ddeb550f133e657854b3b6f89d96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409626"
---
# <a name="eventreceiver"></a>event_receiver

创建事件接收器（接收器）。

## <a name="syntax"></a>语法

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>参数

*type*<br/>
以下值之一的枚举：

- `native` 对于非托管 C /C++代码 （本机类的默认值）。

- `com` ，用于 COM 代码。 此值需要包含以下头文件：

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
指定*layout_dependent*仅当`type` = **com**。 *layout_dependent*是一个布尔值：

- **true**事件接收方必须完全匹配这些到将挂钩在事件源中表示的委托签名。 事件接收方处理程序名称必须与匹配相关的事件源接口中指定的名称。 必须使用`coclass`时*layout_dependent*是**true**。 它是指定稍微更高效 **，则返回 true**。

- **false** （默认值） 意味着，调用约定和存储类 (虚拟、 静态的以及其他) 无需匹配的事件方法和处理程序; 也不执行操作的处理程序名称需要匹配的事件源接口方法名称。

## <a name="remarks"></a>备注

**Event_receiver** C++属性指定的类或结构应用于会是事件接收器，使用视觉对象C++统一的事件模型。

**event_receiver**用于[event_source](event-source.md)属性和[__hook](../../cpp/hook.md)并[__unhook](../../cpp/unhook.md)关键字。 使用`event_source`创建事件源。 使用 **__hook**事件接收器的方法将关联 （"挂钩"） 的事件源的事件的事件接收方方法中。 使用 **__unhook**若要取消关联它们。

*layout_dependent*只能指定适用于 COM 事件接收器 (`type`=**com**)。 默认值为*layout_dependent*是**false**。

> [!NOTE]
> 模板类或结构不能包含事件。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**|
|**可重复**|否|
|**必需的特性**|`coclass` 当*layout_dependent*=**，则返回 true**|
|**无效的特性**|None|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[编译器特性](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[类特性](class-attributes.md)