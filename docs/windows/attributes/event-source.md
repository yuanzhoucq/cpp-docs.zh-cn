---
title: event_source （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_source
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
ms.openlocfilehash: a7231b01cd341bbc04bcccd3c2198d1a76dd5e39
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232763"
---
# <a name="event_source"></a>event_source

创建事件源。

## <a name="syntax"></a>语法

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>参数

*type*<br/>
以下值之一的枚举：

- `native` ，用于非托管 C/C++ 代码（非托管类的默认值）。

- `com` ，用于 COM 代码。 当 `coclass` = `type`=`com`。 此值需要包含以下头文件：

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optimize*<br/>
当*类型*为时 `native` ，你可以指定 `optimize=size` ，以指示对于类中的所有事件存在4个字节的存储（最小值）或 `optimize=speed` （默认值）以指示存在 4 * （事件数）个字节的存储。

*decorate*<br/>
如果*type*为 `native` ，则可以指定 `decorate=false` ，以指示合并（. .mrg）文件中的扩展名称不应包含封闭类名称。 [/Fx](../../build/reference/fx-merge-injected-code.md) 允许生成 .mrg 文件。 `decorate=false`（这是默认值）会导致合并文件中具有完全限定的类型名称。

## <a name="remarks"></a>备注

**event_source** C++ 属性指定应用它的类或结构会是事件源。

**event_source** 与 [event_receiver](event-receiver.md) 属性和 [__event](../../cpp/event.md) 关键字结合使用。 用于 `event_receiver` 创建事件接收器。 对 **`__event`** 事件源中的方法使用可将这些方法指定为事件。

> [!NOTE]
> 模板类或结构不能包含事件。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**`class`**, **`struct`**|
|**且**|否|
|**必需属性**|**组件类**`type`=`com`|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[编译器特性](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[类特性](class-attributes.md)
