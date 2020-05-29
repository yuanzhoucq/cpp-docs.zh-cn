---
title: event_source （C++ COM 特性）
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
ms.openlocfilehash: e187e57f21e9c94068c0b3396b93deed617fef2a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167064"
---
# <a name="event_source"></a>event_source

创建事件源。

## <a name="syntax"></a>语法

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>parameters

type<br/>
以下值之一的枚举：

- `native` ，用于非托管 C/C++ 代码（非托管类的默认值）。

- `com` ，用于 COM 代码。 当 `coclass` = `type`=`com`。 此值需要包含以下头文件：

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optimize*<br/>
当*类型*为 `native`时，可以指定 `optimize=size`，以指示类或 `optimize=speed` （默认值）中的所有事件有4个字节的存储（最小值），以指示存在 4 * （事件数）个字节的存储。

*decorate*<br/>
当*类型*`native`时，可以指定 `decorate=false`，以指示已合并（. .mrg）文件中的扩展名称不应包含封闭类名称。 [/Fx](../../build/reference/fx-merge-injected-code.md) 允许生成 .mrg 文件。 `decorate=false`（这是默认值）会导致合并文件中具有完全限定的类型名称。

## <a name="remarks"></a>备注

**event_source** C++ 属性指定应用它的类或结构会是事件源。

**event_source** 与 [event_receiver](event-receiver.md) 属性和 [__event](../../cpp/event.md) 关键字结合使用。 使用 `event_receiver` 创建事件接收器。 对事件源中的方法使用 **__event** ，以将这些方法指定为事件。

> [!NOTE]
> 模板类或结构不能包含事件。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**class**、 **struct**|
|**可重复**|否|
|**必需的特性**|`type`=时的**coclass** `com`|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[编译器特性](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[类特性](class-attributes.md)
