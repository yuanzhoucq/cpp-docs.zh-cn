---
title: "Typedef, Enum, Union, and Struct Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "union attributes"
  - "attributes [C++], reference topics"
  - "struct attributes"
  - "typedef attributes"
  - "enum attributes"
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Typedef, Enum, Union, and Struct Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下特性应用于 [typedef](http://msdn.microsoft.com/zh-cn/cc96cf26-ba93-4179-951e-695d1f5fdcf1)、 [结构](../cpp/struct-cpp.md)和 [枚举](../cpp/enumerations-cpp.md) C\+\+ 关键字。  
  
### typedef  
  
|特性|说明|  
|--------|--------|  
|[case](../windows/case-cpp.md)|使用 [switch\_type](../windows/switch-type.md) 属性。 **联合**。|  
|[custom](../windows/custom-cpp.md)|使您可以定义拥有该属性。|  
|[export](../windows/export.md)|在 .idl 文件中创建一个数据结构将。|  
|[first\_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|  
|[helpcontext](../windows/helpcontext.md)|指定可获取有关此元素的用户查看信息在帮助文件的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置帮助文件的名称类型库。|  
|[helpstring](../windows/helpstring.md)|指定一个字符串，该字符串用来描述它所应用的元素。|  
|[library\_block](../windows/library-block.md)|放在 .idl 文件的库中的构造块。|  
|[PTR](../windows/ptr.md)|指定指针作为完整的指针。|  
|[public](../windows/public-cpp-attributes.md)|确保 typedef 将进入类型库，即使未引用从 .idl 文件内。|  
|[ref](../windows/ref-cpp.md)|标识引用指针。|  
|[switch\_is](../windows/switch-is.md)|指定作为选择联合成员的联合的表达式或标识符具有识别力。|  
|[switch\_type](../windows/switch-type.md)|标识为该联合使用的变量的类型具有识别力。|  
|[单个](../windows/unique-cpp.md)|指定一个指针。|  
|[wire\_marshal](../windows/wire-marshal.md)|指定在传输将使用而不是一个特定的数据类型的数据类型。|  
  
### enum  
  
|特性|说明|  
|--------|--------|  
|[custom](../windows/custom-cpp.md)|使您可以定义拥有该属性。|  
|[export](../windows/export.md)|在 .idl 文件中创建一个数据结构将。|  
|[uuid](../windows/uuid-cpp-attributes.md)|为类或接口指定唯一 ID。|  
|[v1\_enum](../windows/v1-enum.md)|命令，指定的枚举类型传输作为 32 位实体，而不是该 16 位默认值。|  
  
### union  
  
|特性|说明|  
|--------|--------|  
|[custom](../windows/custom-cpp.md)|使您可以定义拥有该属性。|  
|[export](../windows/export.md)|在 .idl 文件中创建一个数据结构将。|  
|[first\_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|  
|[last\_is](../windows/last-is.md)|指定要传输的最后一个数组元素的索引。|  
|[length\_is](../windows/length-is.md)|指定数组元素数会传输的。|  
|[max\_is](../windows/max-is.md)|指定有效的数组索引的最大值。|  
|[size\_is](../windows/size-is.md)|为大小的指针、大小的指向大小的指针和单项或多维数组指定内存大小分配。|  
|[单个](../windows/unique-cpp.md)|指定一个指针。|  
|[uuid](../windows/uuid-cpp-attributes.md)|为类或接口指定唯一 ID。|  
  
### Nonencapsulated 联合  
  
|特性|说明|  
|--------|--------|  
|[ms\_union](../windows/ms-union.md)|控件 nonencapsulated 联合的网络数据表示形式对齐。|  
|[no\_injected\_text](../windows/no-injected-text.md)|由于属性使用，以防止编译器插入代码。|  
  
### struct  
  
|特性|说明|  
|--------|--------|  
|[可聚集的](../windows/aggregatable.md)|指示类支持聚合。|  
|[聚合](../windows/aggregates.md)|指示控件复合目标类。|  
|[appobject](../windows/appobject.md)|标识 coclass 为应用程序对象，与完整的 .exe 应用程序，并指示 coclass 的功能和特性是全局可用此类型库。|  
|[coclass](../windows/coclass.md)|创建 Activex 控件。|  
|[com\_interface\_entry](../windows/com-interface-entry-cpp.md)|添加接口项添加到 COM 映射。|  
|[控件](../windows/control.md)|指定用户定义的类型是控件。|  
|[custom](../windows/custom-cpp.md)|使您可以定义拥有该属性。|  
|[db\_column](../windows/db-column.md)|将指定的列设置为行集合。|  
|[db\_command](../windows/db-command.md)|创建一个 OLE DB 命令。|  
|[db\_param](../windows/db-param.md)|将指定的成员变量与输入或输出参数并将变量。|  
|[db\_source](../windows/db-source.md)|创建与数据源的连接。|  
|[db\_table](../windows/db-table.md)|打开 OLE DB 表。|  
|[default](../windows/default-cpp.md)|指示在或调度接口中定义的自定义 coclass 表示默认可编程接口。|  
|[defaultvtable](../windows/defaultvtable.md)|定义一个接口作为控件的默认 vtable 接口。|  
|[event\_receiver](../windows/event-receiver.md)|创建一个事件接收器。|  
|[event\_source](../windows/event-source.md)|创建一个事件源。|  
|[export](../windows/export.md)|在 .idl 文件中创建一个数据结构将。|  
|[first\_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|  
|[hidden](../windows/hidden.md)|指示该项目在面向用户的浏览器存在，但不应显示。|  
|[implements\_category](../windows/implements-category.md)|标识实现了类的组件类。|  
|[last\_is](../windows/last-is.md)|指定要传输的最后一个数组元素的索引。|  
|[length\_is](../windows/length-is.md)|指定数组元素数会传输的。|  
|[max\_is](../windows/max-is.md)|指定有效的数组索引的最大值。|  
|[requires\_category](../windows/requires-category.md)|指定目标类必需的组件类。|  
|[size\_is](../windows/size-is.md)|为大小的指针、大小的指向大小的指针和单项或多维数组指定内存大小分配。|  
|[source](../windows/source-cpp.md)|在类中，指定 COM 对象的源接口的连接点。  在属性或方法，指示成员返回作为事件源的对象或变量。|  
|[线程处理](../windows/threading-cpp.md)|为 COM 对象指定线程模型。|  
|[单个](../windows/unique-cpp.md)|指定一个指针。|  
|[uuid](../windows/uuid-cpp-attributes.md)|为类或接口指定唯一 ID。|  
|[version](../windows/version-cpp.md)|标识在类中的多个版本的特定版本。|  
|[vi\_progid](../windows/vi-progid.md)|指定 ProgID 的一个版本中立性窗体。|  
  
## 请参阅  
 [Attributes by Usage](../windows/attributes-by-usage.md)