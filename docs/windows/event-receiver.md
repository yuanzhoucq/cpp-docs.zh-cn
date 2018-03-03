---
title: "event_receiver |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.event_receiver
dev_langs:
- C++
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50ea26172e2f5112e760aa02d9247d07afbead2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="eventreceiver"></a>event_receiver
创建事件接收器（接收器）。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ event_receiver(  
   type   
   [, layout_dependent=false]   
) ]  
```  
  
#### <a name="parameters"></a>参数  
 `type`  
 以下值之一的枚举：  
  
-   `native`对于非托管 C/c + + 代码 （本机类的默认值）。  
  
-   `com` ，用于 COM 代码。 此值需要包含以下头文件：  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **layout_dependent**  
 指定*layout_dependent*才`type` = **com**。*layout_dependent*是一个布尔值：  
  
-   **true**意味着，委托的签名接收方必须完全匹配那些到将挂钩到事件源的事件中。 事件接收器处理程序的名称必须与匹配相关的事件源接口中指定的名称。 必须使用**组件类**时*layout_dependent*是**true**。 它是指定略有更高效**true**。  
  
-   **false** （默认值） 意味着的调用约定和存储类 (虚拟、 静态、 等) 不需要匹配事件方法并处理程序; 也不处理程序的名称需要匹配事件源接口方法名称。  
  
## <a name="remarks"></a>备注  
 **Event_receiver** c + + 特性指定的类或结构应用到的将是事件接收器，使用 Visual c + + 统一的事件模型。  
  
 **event_receiver**用于[event_source](../windows/event-source.md)属性和[__hook](../cpp/hook.md)和[__unhook](../cpp/unhook.md)关键字。 使用**event_source**创建事件源。 使用`__hook`事件接收器的方法将关联 （"挂钩"） 中的事件源的事件的事件接收器方法内。 使用`__unhook`取消它们。  
  
 *layout_dependent*仅指定适用于 COM 事件接收器 (`type`=**com**)。 默认值为*layout_dependent*是**false**。  
  
> [!NOTE]
>  模板类或结构不能包含事件。  
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**， `struct`|  
|**可重复**|否|  
|**必需的特性**|**组件类**时*layout_dependent*=**true**|  
|**无效的特性**|无|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [编译器特性](../windows/compiler-attributes.md)   
 [event_source](../windows/event-source.md)   
 [__event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [类特性](../windows/class-attributes.md)   
