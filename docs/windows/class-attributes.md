---
title: "类特性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- attributes [C++], class attributes
- class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9d6883774f6deeae2d8c372b68362c743d206eb9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="class-attributes"></a>类特性
下列属性适用于[类](../cpp/class-cpp.md)c + + 关键字。  
  
|特性|描述|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|指示的类支持聚合。|  
|[aggregates](../windows/aggregates.md)|指示控件聚合目标类。|  
|[appobject](../windows/appobject.md)|标识为一个应用程序对象，它是一个完整的.exe 应用程序中，与关联和指示不存在的函数和属性组件类全局在此类型库中的组件类。|  
|[case](../windows/case-cpp.md)|与使用[switch_type](../windows/switch-type.md)联合中的属性。|  
|[coclass](../windows/coclass.md)|创建 ActiveX 控件。|  
|[com_interface_entry](../windows/com-interface-entry-cpp.md)|将一个接口条目添加到 COM 映射。|  
|[control](../windows/control.md)|指定的用户定义的类型是一个控件。|  
|[自定义](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[db_command](../windows/db-command.md)|创建 OLE DB 命令。|  
|[db_param](../windows/db-param.md)|将指定的成员变量与一个输入或输出参数相关联，并分隔变量。|  
|[db_source](../windows/db-source.md)|创建与数据源的连接。|  
|[db_table](../windows/db-table.md)|将打开一个 OLE DB 表。|  
|[default](../windows/default-cpp.md)|指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。|  
|[defaultvtable](../windows/defaultvtable.md)|为控件的默认 vtable 接口中定义一个接口。|  
|[event_receiver](../windows/event-receiver.md)|创建事件接收器。|  
|[event_source](../windows/event-source.md)|创建事件源。|  
|[helpcontext](../windows/helpcontext.md)|指定允许用户查看有关此帮助文件中的元素信息的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置类型库的帮助文件的名称。|  
|[helpstringcontext](../windows/helpstringcontext.md)|.Hlp 或.chm 文件中指定的帮助主题的 ID。|  
|[helpstring](../windows/helpstring.md)|指定用于描述应用于元素的字符字符串。|  
|[hidden](../windows/hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|  
|[实现](../windows/implements-cpp.md)|指定强制 IDL 组件类的成员的调度接口。|  
|[implements_category](../windows/implements-category.md)|指定类的实现的组件类别。|  
|[模块](../windows/module-cpp.md)|定义.Idl 文件中的库块。|  
|[noncreatable](../windows/noncreatable.md)|定义本身不能实例化的对象。|  
|[progid](../windows/progid.md)|定义控件的 ProgID。|  
|[registration_script](../windows/registration-script.md)|执行指定的注册脚本。|  
|[requestedit](../windows/requestedit.md)|该值指示属性是否支持**OnRequestEdit**通知。|  
|[源](../windows/source-cpp.md)|指定控件的连接点的源接口的类上。 属性或方法上,**源**属性指示的成员返回的对象或作为源的事件的变体。|  
|[support_error_info](../windows/support-error-info.md)|支持的错误报告目标对象。|  
|[线程处理](../windows/threading-cpp.md)|指定控件的线程模型。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定为类或接口的唯一 ID。|  
|[version](../windows/version-cpp.md)|标识的类的多个版本之间的特定版本。|  
|[vi_progid](../windows/vi-progid.md)|指定独立于版本的窗体的 ProgID。|  
  
## <a name="see-also"></a>另请参阅  
 [按用法分的特性](../windows/attributes-by-usage.md)