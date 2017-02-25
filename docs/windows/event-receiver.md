---
title: "event_receiver | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.event_receiver"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "event_receiver attribute"
  - "event receivers"
  - "events [C++], event receivers (sinks)"
  - "event handling [C++], attributes"
  - "event handling [C++], creating receiver"
  - "event sinks, creating"
  - "event sinks"
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# event_receiver
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建一个事件接收器 \(接收器\)。  
  
## 语法  
  
```  
  
      [ event_receiver(  
   type   
   [, layout_dependent=false]   
) ]  
```  
  
#### 参数  
 `type`  
 枚举下列值之一:  
  
-   非托管 C\/C\+\+ 代码 \(本机类的默认`native` \)。  
  
-   COM 代码的`com` 。  此值需要包括以下头文件:  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **layout\_dependent**  
 指定 *layout\_dependent* ，仅当 `type`\=**COM**。  *layout\_dependent* 布尔值:  
  
-   **true** 意味着委托的签名事件接收器的必须与它们在事件源挂钩的项。  事件接收器处理程序名称必须与相关事件源接口指定的名称。  必须使用 **coclass** ，当 *layout\_dependent* 是 **true**。  效率稍高的指定 **true**。  
  
-   **错误** \(默认值\) 表示调用约定和存储类 \(虚方法，静态和其他\) 不必与操作方法和处理程序;也不需要名称与事件源接口方法名称的处理程序。  
  
## 备注  
 **event\_receiver** C\+\+ 特性指定它是应用的类或结构将为事件接收器，使用 Visual C\+\+ 统一的事件模型，。  
  
 **event\_receiver** 使用 [event\_source](../windows/event-source.md) 属性和 [\_\_hook](../cpp/hook.md) 和 [\_\_unhook](../cpp/unhook.md) 关键字。  使用 **event\_source** 创建事件源。  使用将事件接收器的方法中 `__hook` 关联 \(“挂钩”\) 事件接收器方法添加到事件源的事件。  使用 `__unhook` 取消它们。  
  
 *layout\_dependent* 用于 COM 事件接收器 \(`type`\=**COM**\) 仅指定。  *layout\_dependent 的* 默认值为 **错误**。  
  
> [!NOTE]
>  模板类或结构不能包含事件。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`|  
|**可重复**|否|  
|**必需的特性**|**coclass** ，当 layout\_dependent\=**true**|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [event\_source](../windows/event-source.md)   
 [\_\_event](../cpp/event.md)   
 [\_\_hook](../cpp/hook.md)   
 [\_\_unhook](../cpp/unhook.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)