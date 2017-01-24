---
title: "event_source | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.event_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件处理, 属性"
  - "事件日志, 事件源"
  - "事件源, 创建"
  - "event_source 特性"
  - "事件源"
  - "事件处理, 创建事件源"
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# event_source
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建事件源。  
  
## 语法  
  
```  
  
       [ event_source(  
       type,  
optimize=[speed | size],  
decorate=[true | false]) ]  
```  
  
#### 参数  
 `type`  
 以下值之一的枚举：  
  
-   `native`，用于非托管 C\/C\+\+ 代码（非托管类的默认值）。  
  
-   `com`，用于 COM 代码。 当 `type`\=`com` 时，必须使用 `coclass`。 此值需要包含以下头文件：  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **optimize**  
 当 `type` 是 **native** 时，可以指定 **optimize\=size** 以指示对于类中的所有事件存在 4 个字节的存储（最小值），也可以指定 **optimize\=speed**（默认值）以指示存在 4 \* \(事件数\) 个字节的存储。  
  
 **decorate**  
 当 `type` 是 **native** 时，可以指定 **decorate\=false**，以指示合并 \(.mrg\) 文件中的扩展名称不应包含封闭类名。[\/Fx](../build/reference/fx-merge-injected-code.md) 允许生成 .mrg 文件。**decorate\=false**（这是默认值）会导致合并文件中存在完全限定的类型名称。  
  
## 备注  
 **event\_source** C\+\+ 属性指定应用它的类或结构会是事件源。  
  
 **event\_source** 与 [event\_receiver](../windows/event-receiver.md) 属性和 [\_\_event](../cpp/event.md) 关键字结合使用。 使用 **event\_receiver** 可创建事件接收器。 对事件源中的方法使用 `__event` 可将这些方法指定为事件。  
  
> [!NOTE]
>  模板类或结构不能包含事件。  
  
## 要求  
  
### 特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**，`struct`|  
|**可重复**|No|  
|**必需的特性**|**coclass**（当 `type`\=**com** 时）|  
|**无效的特性**|无|  
  
 有关详细信息，请参见[特性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [event\_receiver](../windows/event-receiver.md)   
 [\_\_event](../cpp/event.md)   
 [\_\_hook](../cpp/hook.md)   
 [\_\_unhook](../cpp/unhook.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)