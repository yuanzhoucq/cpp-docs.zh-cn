---
title: event_receiver （c + + COM 特性）
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
ms.openlocfilehash: fb17eaa5d94636cedd650eb1bfb393d7c09e4fcc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217267"
---
# <a name="event_receiver"></a>event_receiver

创建事件接收器（接收器）。

## <a name="syntax"></a>语法

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>参数

*type*<br/>
以下值之一的枚举：

- `native`对于非托管 C/c + + 代码（本机类的默认值）。

- `com` ，用于 COM 代码。 此值需要包含以下头文件：

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
仅*layout_dependent*在 `type` = **com**中指定 layout_dependent。 *layout_dependent*是一个布尔值：

- **`true`** 表示事件接收器中的委托的签名必须与事件源中的委托的签名完全匹配。 事件接收器处理程序名称必须与相关事件源接口中指定的名称相匹配。 `coclass` *Layout_dependent*为时，必须使用 **`true`** 。 指定的效率稍有提高 **`true`** 。

- **`false`**（默认值）表示调用约定和存储类（虚拟、静态以及其他）不必与事件方法和处理程序匹配;或处理程序名称不需要与事件源接口方法名称匹配。

## <a name="remarks"></a>备注

**Event_receiver** c + + 属性指定应用它的类或结构将是使用 Visual C++ 统一事件模型的事件接收器。

**event_receiver**与[event_source](event-source.md)特性和[__hook](../../cpp/hook.md)和[__unhook](../../cpp/unhook.md)关键字一起使用。 用于 `event_source` 创建事件源。 **`__hook`** 在事件接收器的方法中使用，将事件接收器方法关联（"挂钩"）到事件源的事件。 使用取消关联 **`__unhook`** 。

*layout_dependent*仅为 com 事件接收器（ `type` = **com**）指定 layout_dependent。 *Layout_dependent*的默认值为 **`false`** 。

> [!NOTE]
> 模板类或结构不能包含事件。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**`class`**, **`struct`**|
|**且**|否|
|**必需属性**|`coclass`当*layout_dependent*=**`true`**|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[编译器特性](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[类特性](class-attributes.md)
