---
title: "Class Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], class attributes"
  - "class attributes"
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Class Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下特性应用于 [类](../cpp/class-cpp.md) C\+\+ 关键字。  
  
|特性|说明|  
|--------|--------|  
|[可聚集的](../windows/aggregatable.md)|指示类支持聚合。|  
|[聚合](../windows/aggregates.md)|指示控件复合目标类。|  
|[appobject](../windows/appobject.md)|标识 coclass 为应用程序对象，与完整的 .exe 应用程序，并指示 coclass 的功能和特性是全局可用此类型库。|  
|[case](../windows/case-cpp.md)|使用 [switch\_type](../windows/switch-type.md) 属性在联合。|  
|[coclass](../windows/coclass.md)|创建 Activex 控件。|  
|[com\_interface\_entry](../windows/com-interface-entry-cpp.md)|添加接口项添加到 COM 映射。|  
|[控件](../windows/control.md)|指定用户定义的类型是控件。|  
|[custom](../windows/custom-cpp.md)|使您可以定义拥有该属性。|  
|[db\_command](../windows/db-command.md)|创建一个 OLE DB 命令。|  
|[db\_param](../windows/db-param.md)|将指定的成员变量与输入或输出参数并将变量。|  
|[db\_source](../windows/db-source.md)|创建与数据源的连接。|  
|[db\_table](../windows/db-table.md)|打开 OLE DB 表。|  
|[default](../windows/default-cpp.md)|指示在或调度接口中定义的自定义 coclass 表示默认可编程接口。|  
|[defaultvtable](../windows/defaultvtable.md)|定义一个接口作为控件的默认 vtable 接口。|  
|[event\_receiver](../windows/event-receiver.md)|创建一个事件接收器。|  
|[event\_source](../windows/event-source.md)|创建一个事件源。|  
|[helpcontext](../windows/helpcontext.md)|指定可获取有关此元素的用户查看信息在帮助文件的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置帮助文件的名称类型库。|  
|[helpstringcontext](../windows/helpstringcontext.md)|在 .hlp 或 .chm 文件指定帮助主题的 ID。|  
|[helpstring](../windows/helpstring.md)|指定一个字符串，该字符串用来描述它所应用的元素。|  
|[hidden](../windows/hidden.md)|指示该项目在面向用户的浏览器存在，但不应显示。|  
|[implements](../windows/implements-cpp.md)|指定强制为 IDL coclass 的成员的调度接口。|  
|[implements\_category](../windows/implements-category.md)|标识实现了类的组件类。|  
|[Module — 模块](../windows/module-cpp.md)|在 .idl 文件中定义了库块。|  
|[不可创建](../windows/noncreatable.md)|定义不能单独实例化的对象。|  
|[progid](../windows/progid.md)|定义控件的 ProgID。|  
|[registration\_script](../windows/registration-script.md)|执行指定的注册脚本。|  
|[requestedit](../windows/requestedit.md)|指示属性支持 **OnRequestEdit** 通知。|  
|[source](../windows/source-cpp.md)|为类指定控件的源接口的连接点。  在属性或方法， **源** 属性指示成员返回作为事件源的对象或变量。|  
|[support\_error\_info](../windows/support-error-info.md)|支持目标对象的错误报告。|  
|[线程处理](../windows/threading-cpp.md)|为控件指定线程模型。|  
|[uuid](../windows/uuid-cpp-attributes.md)|为类或接口指定唯一 ID。|  
|[version](../windows/version-cpp.md)|标识在类中的多个版本的特定版本。|  
|[vi\_progid](../windows/vi-progid.md)|指定 ProgID 的一个版本中立性窗体。|  
  
## 请参阅  
 [Attributes by Usage](../windows/attributes-by-usage.md)