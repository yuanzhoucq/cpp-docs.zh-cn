---
title: Typedef、Enum、Union 和 Struct 属性（C++ COM）
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: fdc380cdc207361a145862f87d809a4bcea01c27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214469"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Typedef、Enum、Union 和 Struct 特性

以下属性适用于[typedef](../../cpp/aliases-and-typedefs-cpp.md)、 [struct](../../cpp/struct-cpp.md)和[enum](../../cpp/enumerations-cpp.md) C++关键字。

### <a name="typedef"></a>typedef

|特性|描述|
|---------------|-----------------|
|[case](case-cpp.md)|与**联合**中的[switch_type](switch-type.md)特性一起使用。|
|[custom](custom-cpp.md)|允许您定义自己的属性。|
|[export](export.md)|导致将数据结构放置在 .idl 文件中。|
|[first_is](first-is.md)|指定要传输的第一个数组元素的索引。|
|[helpcontext](helpcontext.md)|指定一个上下文 ID，该 ID 允许用户在帮助文件中查看有关此元素的信息。|
|[helpfile](helpfile.md)|设置类型库的帮助文件的名称。|
|[helpstring](helpstring.md)|指定一个字符串，用于描述应用该字符串的元素。|
|[library_block](library-block.md)|将构造置于 .idl 文件的库块内。|
|[ptr](ptr.md)|将指针指定为完全指针。|
|[public](public-cpp-attributes.md)|确保 typedef 将进入类型库，即使它未从 .idl 文件中引用。|
|[ref](ref-cpp.md)|标识引用指针。|
|[switch_is](switch-is.md)|指定充当用于选择联合成员的联合判别的表达式或标识符。|
|[switch_type](switch-type.md)|标识用作联合判别的变量的类型。|
|[unique](unique-cpp.md)|指定唯一的指针。|
|[wire_marshal](wire-marshal.md)|指定将用于传输的数据类型，而不是特定于应用程序的数据类型。|

### <a name="enum"></a>enum

|特性|描述|
|---------------|-----------------|
|[custom](custom-cpp.md)|允许您定义自己的属性。|
|[export](export.md)|导致将数据结构放置在 .idl 文件中。|
|[uuid](uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|
|[v1_enum](v1-enum.md)|指示指定的枚举类型传输为32位实体，而不是16位默认值。|

### <a name="union"></a>union

|特性|描述|
|---------------|-----------------|
|[custom](custom-cpp.md)|允许您定义自己的属性。|
|[export](export.md)|导致将数据结构放置在 .idl 文件中。|
|[first_is](first-is.md)|指定要传输的第一个数组元素的索引。|
|[last_is](last-is.md)|指定要传输的最后一个数组元素的索引。|
|[length_is](length-is.md)|指定要传输的数组元素的数目。|
|[max_is](max-is.md)|指定有效数组索引的最大值。|
|[size_is](size-is.md)|指定分配给大小指针的内存大小、大小指针的大小指针以及单数组或多维数组。|
|[unique](unique-cpp.md)|指定唯一的指针。|
|[uuid](uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|

### <a name="nonencapsulated-union"></a>Nonencapsulated 联合

|特性|描述|
|---------------|-----------------|
|[ms_union](ms-union.md)|控制 nonencapsulated 联合的网络数据表示形式的对齐方式。|
|[no_injected_text](no-injected-text.md)|阻止编译器将代码注入到属性使用的结果中。|

### <a name="struct"></a>struct

|特性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|指示类支持聚合。|
|[aggregates](aggregates.md)|指示控件聚合目标类。|
|[appobject](appobject.md)|将 coclass 标识为与完整 .exe 应用程序关联的应用程序对象，并指示 coclass 的函数和属性在此类型库中全局可用。|
|[coclass](coclass.md)|创建 ActiveX 控件。|
|[com_interface_entry](com-interface-entry-cpp.md)|向 COM 映射添加接口条目。|
|[control](control.md)|指定用户定义类型为控件。|
|[custom](custom-cpp.md)|允许您定义自己的属性。|
|[db_column](db-column.md)|将指定列绑定到行集。|
|[db_command](db-command.md)|创建 OLE DB 命令。|
|[db_param](db-param.md)|将指定的成员变量与输入或输出参数关联，并将变量分隔。|
|[db_source](db-source.md)|创建与数据源的连接。|
|[db_table](db-table.md)|打开 OLE DB 表。|
|[default](default-cpp.md)|指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。|
|[defaultvtable](defaultvtable.md)|将接口定义为控件的默认 vtable 接口。|
|[event_receiver](event-receiver.md)|创建事件接收器。|
|[event_source](event-source.md)|创建事件源。|
|[export](export.md)|导致将数据结构放置在 .idl 文件中。|
|[first_is](first-is.md)|指定要传输的第一个数组元素的索引。|
|[hidden](hidden.md)|指示该项存在，但不应在面向用户的浏览器中显示。|
|[implements_category](implements-category.md)|指定类实现的组件类别。|
|[last_is](last-is.md)|指定要传输的最后一个数组元素的索引。|
|[length_is](length-is.md)|指定要传输的数组元素的数目。|
|[max_is](max-is.md)|指定有效数组索引的最大值。|
|[requires_category](requires-category.md)|指定目标类的必需组件类别。|
|[size_is](size-is.md)|指定分配给大小指针的内存大小、大小指针的大小指针以及单数组或多维数组。|
|[source](source-cpp.md)|在类上，为连接点指定 COM 对象的源接口。 在属性或方法上，指示成员返回作为事件来源的对象或变体。|
|[threading](threading-cpp.md)|指定 COM 对象的线程模型。|
|[unique](unique-cpp.md)|指定唯一的指针。|
|[uuid](uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|
|[版本](version-cpp.md)|标识类的多个版本中的特定版本。|
|[vi_progid](vi-progid.md)|指定 ProgID 的与版本无关的形式。|

## <a name="see-also"></a>请参阅

[按用法分的特性](attributes-by-usage.md)
