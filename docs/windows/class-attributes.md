---
title: 类特性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], class attributes
- class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0a2fe111028f952482dbd6b2eedebc157d39a9a4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645170"
---
# <a name="class-attributes"></a>类特性
以下属性应用于[类](../cpp/class-cpp.md)c + + 关键字。  
  
|特性|描述|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|指示该类支持聚合。|  
|[aggregates](../windows/aggregates.md)|指示控件聚合的目标类。|  
|[appobject](../windows/appobject.md)|标识作为应用程序对象，这些程序与完整.exe 的应用程序，并指示的函数和组件类的属性全球可用此类型库中的组件类。|  
|[case](../windows/case-cpp.md)|用于[switch_type](../windows/switch-type.md)联合中的属性。|  
|[coclass](../windows/coclass.md)|创建 ActiveX 控件。|  
|[com_interface_entry](../windows/com-interface-entry-cpp.md)|将接口条目添加到 COM 映射。|  
|[control](../windows/control.md)|指定用户定义类型为控件。|  
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[db_command](../windows/db-command.md)|创建 OLE DB 命令。|  
|[db_param](../windows/db-param.md)|指定的成员变量相关联的输入或输出参数和分隔变量。|  
|[db_source](../windows/db-source.md)|创建与数据源的连接。|  
|[db_table](../windows/db-table.md)|将打开一个 OLE DB 表。|  
|[default](../windows/default-cpp.md)|指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。|  
|[defaultvtable](../windows/defaultvtable.md)|为控件的默认 vtable 接口定义的接口。|  
|[event_receiver](../windows/event-receiver.md)|创建事件接收器。|  
|[event_source](../windows/event-source.md)|创建事件源。|  
|[helpcontext](../windows/helpcontext.md)|指定允许用户查看有关中此元素的信息的上下文 ID**帮助**文件。|  
|[helpfile](../windows/helpfile.md)|设置类型库的帮助文件的名称。|  
|[helpstringcontext](../windows/helpstringcontext.md)|在.hlp 或.chm 文件中指定的帮助主题的 ID。|  
|[helpstring](../windows/helpstring.md)|指定一个字符串，用于描述应用该字符串的元素。|  
|[hidden](../windows/hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|  
|[实现](../windows/implements-cpp.md)|指定强制 IDL 组件类的成员的调度接口。|  
|[implements_category](../windows/implements-category.md)|指定类的实现的组件类别。|  
|[模块](../windows/module-cpp.md)|定义.Idl 文件中的库块。|  
|[noncreatable](../windows/noncreatable.md)|定义不能实例化本身的对象。|  
|[progid](../windows/progid.md)|定义控件的 ProgID。|  
|[registration_script](../windows/registration-script.md)|执行指定的注册脚本。|  
|[requestedit](../windows/requestedit.md)|指示该属性支持`OnRequestEdit`通知。|  
|[source](../windows/source-cpp.md)|指定连接点的控件的源接口的类上。 在属性或方法，`source`属性指示该成员返回的对象或`VARIANT`，它是事件的源。|  
|[support_error_info](../windows/support-error-info.md)|支持的错误报告目标对象。|  
|[线程处理](../windows/threading-cpp.md)|指定控件的线程模型。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|  
|[version](../windows/version-cpp.md)|标识类的多个版本间的特定版本。|  
|[vi_progid](../windows/vi-progid.md)|指定独立于版本的窗体的 ProgID。|  
  
## <a name="see-also"></a>请参阅  
 [按用法分的特性](../windows/attributes-by-usage.md)