---
title: Typedef、 Enum、 Union 和 Struct 特性 |Microsoft Docs
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
ms.openlocfilehash: 2e4e8ad94e96c6bfc45102f1c970476c484d756f
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649118"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Typedef、Enum、Union 和 Struct 特性
以下属性应用于[typedef](http://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1)，[结构](../cpp/struct-cpp.md)，并[枚举](../cpp/enumerations-cpp.md)c + + 关键字。  
  
### <a name="typedef"></a>typedef  
  
|特性|描述|  
|---------------|-----------------|  
|[case](../windows/case-cpp.md)|用于[switch_type](../windows/switch-type.md)属性中**union**。|  
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[export](../windows/export.md)|导致要放置在.idl 文件中的数据结构。|  
|[first_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|  
|[helpcontext](../windows/helpcontext.md)|指定允许用户查看有关此帮助文件中的元素的信息的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置类型库的帮助文件的名称。|  
|[helpstring](../windows/helpstring.md)|指定一个字符串，用于描述应用该字符串的元素。|  
|[library_block](../windows/library-block.md)|将放置在.idl 文件的库块中的构造。|  
|[ptr](../windows/ptr.md)|将一个指针，指定为完整的指针。|  
|[public](../windows/public-cpp-attributes.md)|可确保即使它未从引用的.idl 文件中，一个 typedef 将转到类型库。|  
|[ref](../windows/ref-cpp.md)|标识引用指针。|  
|[switch_is](../windows/switch-is.md)|指定的表达式或作为联合判别选择联合成员的标识符。|  
|[switch_type](../windows/switch-type.md)|标识用作联合判别变量的类型。|  
|[unique](../windows/unique-cpp.md)|指定一个唯一指针。|  
|[wire_marshal](../windows/wire-marshal.md)|指定将用于传输而不是特定于应用程序的数据类型的数据类型。|  
  
### <a name="enum"></a>enum  
  
|特性|描述|  
|---------------|-----------------|  
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[export](../windows/export.md)|导致要放置在.idl 文件中的数据结构。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|  
|[v1_enum](../windows/v1-enum.md)|指示指定的枚举的类型作为一个 32 位实体，而不是 16 位默认传输。|  
  
### <a name="union"></a>union  
  
|特性|描述|  
|---------------|-----------------|  
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[export](../windows/export.md)|导致要放置在.idl 文件中的数据结构。|  
|[first_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|  
|[last_is](../windows/last-is.md)|指定要传输的最后一个数组元素的索引。|  
|[length_is](../windows/length-is.md)|指定要传输的数组元素数。|  
|[max_is](../windows/max-is.md)|指定有效的数组索引的最大值。|  
|[size_is](../windows/size-is.md)|指定的内存大小为固定大小的指针分配、 调整大小的指针和单字节或多维数组的指针。|  
|[unique](../windows/unique-cpp.md)|指定一个唯一指针。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|  
  
### <a name="nonencapsulated-union"></a>Nonencapsulated 的联合  
  
|特性|描述|  
|---------------|-----------------|  
|[ms_union](../windows/ms-union.md)|控制 nonencapsulated 联合的网络数据表示形式对齐方式。|  
|[no_injected_text](../windows/no-injected-text.md)|禁止编译器注入代码作为特性使用结果。|  
  
### <a name="struct"></a>struct  
  
|特性|描述|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|指示该类支持聚合。|  
|[aggregates](../windows/aggregates.md)|指示控件聚合的目标类。|  
|[appobject](../windows/appobject.md)|标识作为应用程序对象，这些程序与完整.exe 的应用程序，并指示的函数和组件类的属性全球可用此类型库中的组件类。|  
|[coclass](../windows/coclass.md)|创建 ActiveX 控件。|  
|[com_interface_entry](../windows/com-interface-entry-cpp.md)|将接口条目添加到 COM 映射。|  
|[control](../windows/control.md)|指定用户定义类型为控件。|  
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[db_column](../windows/db-column.md)|将指定的列绑定到行集。|  
|[db_command](../windows/db-command.md)|创建 OLE DB 命令。|  
|[db_param](../windows/db-param.md)|指定的成员变量相关联的输入或输出参数和分隔变量。|  
|[db_source](../windows/db-source.md)|创建与数据源的连接。|  
|[db_table](../windows/db-table.md)|将打开一个 OLE DB 表。|  
|[default](../windows/default-cpp.md)|指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。|  
|[defaultvtable](../windows/defaultvtable.md)|为控件的默认 vtable 接口定义的接口。|  
|[event_receiver](../windows/event-receiver.md)|创建事件接收器。|  
|[event_source](../windows/event-source.md)|创建事件源。|  
|[export](../windows/export.md)|导致要放置在.idl 文件中的数据结构。|  
|[first_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|  
|[hidden](../windows/hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|  
|[implements_category](../windows/implements-category.md)|指定类的实现的组件类别。|  
|[last_is](../windows/last-is.md)|指定要传输的最后一个数组元素的索引。|  
|[length_is](../windows/length-is.md)|指定要传输的数组元素数。|  
|[max_is](../windows/max-is.md)|指定有效的数组索引的最大值。|  
|[requires_category](../windows/requires-category.md)|指定目标类的所需的组件类别。|  
|[size_is](../windows/size-is.md)|指定的内存大小为固定大小的指针分配、 调整大小的指针和单字节或多维数组的指针。|  
|[source](../windows/source-cpp.md)|在类上，指定连接点的 COM 对象的源接口。 在属性或方法，指示该成员返回的对象或为事件源的变体。|  
|[线程处理](../windows/threading-cpp.md)|指定 COM 对象的线程处理模型。|  
|[unique](../windows/unique-cpp.md)|指定一个唯一指针。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|  
|[version](../windows/version-cpp.md)|标识类的多个版本间的特定版本。|  
|[vi_progid](../windows/vi-progid.md)|指定独立于版本的窗体的 ProgID。|  
  
## <a name="see-also"></a>请参阅  
 [按用法分的特性](../windows/attributes-by-usage.md)