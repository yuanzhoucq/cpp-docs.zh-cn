---
title: Typedef、 Enum、 Union 和 Struct 特性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- union attributes
- attributes [C++], reference topics
- struct attributes
- typedef attributes
- enum attributes
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c14881afd000dc5fb4223a2ecfa9dcdc67e7b541
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Typedef、Enum、Union 和 Struct 特性
下列属性适用于[typedef](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1)，[结构](../cpp/struct-cpp.md)，和[枚举](../cpp/enumerations-cpp.md)c + + 关键字。  
  
### <a name="typedef"></a>typedef  
  
|特性|描述|  
|---------------|-----------------|  
|[case](../windows/case-cpp.md)|与使用[switch_type](../windows/switch-type.md)属性中**联合**。|  
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[export](../windows/export.md)|会导致数据结构，用于放置在.idl 文件。|  
|[first_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|  
|[helpcontext](../windows/helpcontext.md)|指定允许用户查看有关此帮助文件中的元素信息的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置类型库的帮助文件的名称。|  
|[helpstring](../windows/helpstring.md)|指定用于描述应用于元素的字符字符串。|  
|[library_block](../windows/library-block.md)|将.idl 文件的库块中的构造。|  
|[ptr](../windows/ptr.md)|将一个指针指定为完整的指针。|  
|[public](../windows/public-cpp-attributes.md)|可确保即使它未从引用.idl 文件中，typedef 将转到类型库。|  
|[ref](../windows/ref-cpp.md)|标识引用指针。|  
|[switch_is](../windows/switch-is.md)|指定的表达式或充当选择联合成员联合判别的标识符。|  
|[switch_type](../windows/switch-type.md)|标识用作联合判别变量的类型。|  
|[unique](../windows/unique-cpp.md)|指定一个唯一指针。|  
|[wire_marshal](../windows/wire-marshal.md)|指定将用于传输而不是特定于应用程序的数据类型的数据类型。|  
  
### <a name="enum"></a>enum  
  
|特性|描述|  
|---------------|-----------------|  
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[export](../windows/export.md)|会导致数据结构，用于放置在.idl 文件。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定为类或接口的唯一 ID。|  
|[v1_enum](../windows/v1-enum.md)|指示指定的枚举的类型可为一个 32 位实体，而不是 16 位默认传输。|  
  
### <a name="union"></a>union  
  
|特性|描述|  
|---------------|-----------------|  
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[export](../windows/export.md)|会导致数据结构，用于放置在.idl 文件。|  
|[first_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|  
|[last_is](../windows/last-is.md)|指定要传输的最后一个数组元素的索引。|  
|[length_is](../windows/length-is.md)|指定要传输的数组元素的数目。|  
|[max_is](../windows/max-is.md)|指定有效的数组索引的最大值。|  
|[size_is](../windows/size-is.md)|指定的内存大小为固定大小的指针分配且大小调整了大小的指针和单字节或多维数组的指针。|  
|[unique](../windows/unique-cpp.md)|指定一个唯一指针。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定为类或接口的唯一 ID。|  
  
### <a name="nonencapsulated-union"></a>Nonencapsulated 的联合  
  
|特性|描述|  
|---------------|-----------------|  
|[ms_union](../windows/ms-union.md)|控制 nonencapsulated 联合的网络数据表示形式对齐方式。|  
|[no_injected_text](../windows/no-injected-text.md)|阻止编译器将注入代码作为特性，请使用结果。|  
  
### <a name="struct"></a>struct  
  
|特性|描述|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|指示的类支持聚合。|  
|[aggregates](../windows/aggregates.md)|指示控件聚合目标类。|  
|[appobject](../windows/appobject.md)|标识为一个应用程序对象，它是一个完整的.exe 应用程序中，与关联和指示不存在的函数和属性组件类全局在此类型库中的组件类。|  
|[coclass](../windows/coclass.md)|创建 ActiveX 控件。|  
|[com_interface_entry](../windows/com-interface-entry-cpp.md)|将一个接口条目添加到 COM 映射。|  
|[control](../windows/control.md)|指定的用户定义的类型是一个控件。|  
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[db_column](../windows/db-column.md)|将指定的列绑定到行集。|  
|[db_command](../windows/db-command.md)|创建 OLE DB 命令。|  
|[db_param](../windows/db-param.md)|将指定的成员变量与一个输入或输出参数相关联，并分隔变量。|  
|[db_source](../windows/db-source.md)|创建与数据源的连接。|  
|[db_table](../windows/db-table.md)|将打开一个 OLE DB 表。|  
|[default](../windows/default-cpp.md)|指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。|  
|[defaultvtable](../windows/defaultvtable.md)|为控件的默认 vtable 接口中定义一个接口。|  
|[event_receiver](../windows/event-receiver.md)|创建事件接收器。|  
|[event_source](../windows/event-source.md)|创建事件源。|  
|[export](../windows/export.md)|会导致数据结构，用于放置在.idl 文件。|  
|[first_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|  
|[hidden](../windows/hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|  
|[implements_category](../windows/implements-category.md)|指定类的实现的组件类别。|  
|[last_is](../windows/last-is.md)|指定要传输的最后一个数组元素的索引。|  
|[length_is](../windows/length-is.md)|指定要传输的数组元素的数目。|  
|[max_is](../windows/max-is.md)|指定有效的数组索引的最大值。|  
|[requires_category](../windows/requires-category.md)|指定目标类的必需的组件类别。|  
|[size_is](../windows/size-is.md)|指定的内存大小为固定大小的指针分配且大小调整了大小的指针和单字节或多维数组的指针。|  
|[源](../windows/source-cpp.md)|上一个类，指定连接点的 COM 对象的源接口。 在属性或方法，指示的成员返回的对象或作为源的事件的变体。|  
|[线程处理](../windows/threading-cpp.md)|指定 COM 对象的线程模型。|  
|[unique](../windows/unique-cpp.md)|指定一个唯一指针。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定为类或接口的唯一 ID。|  
|[version](../windows/version-cpp.md)|标识的类的多个版本之间的特定版本。|  
|[vi_progid](../windows/vi-progid.md)|指定独立于版本的窗体的 ProgID。|  
  
## <a name="see-also"></a>请参阅  
 [按用法分的特性](../windows/attributes-by-usage.md)