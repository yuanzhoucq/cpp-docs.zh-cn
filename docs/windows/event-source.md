---
title: event_source |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.event_source
dev_langs:
- C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7e7e287d68bac0fe69417fe21df27ed3231cce6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="eventsource"></a>event_source
创建事件源。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ event_source(  
   type,  
   optimize=[speed | size],  
   decorate=[true | false]  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 `type`  
 以下值之一的枚举：  
  
-   `native` ，用于非托管 C/C++ 代码（非托管类的默认值）。  
  
-   `com` ，用于 COM 代码。 当 `coclass` = `type`=`com`。 此值需要包含以下头文件：  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **optimize**  
 当 `type` 是 **native**时，可以指定 **optimize=size**以指示对于类中的所有事件存在 4 个字节的存储（最小值），也可以指定 **optimize=speed** （默认值）以指示存在 4 * (事件数) 个字节的存储。  
  
 **decorate**  
 当 `type` 是 **native**时，可以指定 **decorate=false**，以指示合并 (.mrg) 文件中的扩展名称不应包含封闭类名。 [/Fx](../build/reference/fx-merge-injected-code.md) 允许生成 .mrg 文件。 **decorate=false**（这是默认值）会导致合并文件中存在完全限定的类型名称。  
  
## <a name="remarks"></a>备注  
 **event_source** C++ 属性指定应用它的类或结构会是事件源。  
  
 **event_source** 与 [event_receiver](../windows/event-receiver.md) 属性和 [__event](../cpp/event.md) 关键字结合使用。 使用 **event_receiver** 可创建事件接收器。 对事件源中的方法使用 `__event` 可将这些方法指定为事件。  
  
> [!NOTE]
>  模板类或结构不能包含事件。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**， `struct`|  
|**可重复**|否|  
|**必需的特性**|**type** = `type`=**com**|  
|**无效的特性**|无|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [编译器特性](../windows/compiler-attributes.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [类特性](../windows/class-attributes.md)   
