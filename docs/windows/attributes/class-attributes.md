---
title: 类特性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
ms.openlocfilehash: d0913d09c51734f5255271c0d06e639810e0cb58
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025411"
---
# <a name="class-attributes"></a>类特性

以下属性应用于[类](../../cpp/class-cpp.md)C++关键字。

|特性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|指示该类支持聚合。|
|[aggregates](aggregates.md)|指示控件聚合的目标类。|
|[appobject](appobject.md)|标识作为应用程序对象，这些程序与完整.exe 的应用程序，并指示的函数和组件类的属性全球可用此类型库中的组件类。|
|[case](case-cpp.md)|用于[switch_type](switch-type.md)联合中的属性。|
|[coclass](coclass.md)|创建 ActiveX 控件。|
|[com_interface_entry](com-interface-entry-cpp.md)|将接口条目添加到 COM 映射。|
|[control](control.md)|指定用户定义类型为控件。|
|[custom](custom-cpp.md)|你可以定义自己的属性。|
|[db_command](db-command.md)|创建 OLE DB 命令。|
|[db_param](db-param.md)|指定的成员变量相关联的输入或输出参数和分隔变量。|
|[db_source](db-source.md)|创建与数据源的连接。|
|[db_table](db-table.md)|将打开一个 OLE DB 表。|
|[default](default-cpp.md)|指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。|
|[defaultvtable](defaultvtable.md)|为控件的默认 vtable 接口定义的接口。|
|[event_receiver](event-receiver.md)|创建事件接收器。|
|[event_source](event-source.md)|创建事件源。|
|[helpcontext](helpcontext.md)|指定允许用户查看有关中此元素的信息的上下文 ID**帮助**文件。|
|[helpfile](helpfile.md)|设置类型库的帮助文件的名称。|
|[helpstringcontext](helpstringcontext.md)|在.hlp 或.chm 文件中指定的帮助主题的 ID。|
|[helpstring](helpstring.md)|指定一个字符串，用于描述应用该字符串的元素。|
|[hidden](hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|
|[implements](implements-cpp.md)|指定强制 IDL 组件类的成员的调度接口。|
|[implements_category](implements-category.md)|指定类的实现的组件类别。|
|[module](module-cpp.md)|定义.Idl 文件中的库块。|
|[noncreatable](noncreatable.md)|定义不能实例化本身的对象。|
|[progid](progid.md)|定义控件的 ProgID。|
|[registration_script](registration-script.md)|执行指定的注册脚本。|
|[requestedit](requestedit.md)|指示该属性支持 `OnRequestEdit` 通知。|
|[source](source-cpp.md)|指定连接点的控件的源接口的类上。 在属性或方法，`source`属性指示该成员返回的对象或`VARIANT`，它是事件的源。|
|[support_error_info](support-error-info.md)|支持的错误报告目标对象。|
|[threading](threading-cpp.md)|指定控件的线程模型。|
|[uuid](uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|
|[版本](version-cpp.md)|标识类的多个版本间的特定版本。|
|[vi_progid](vi-progid.md)|指定独立于版本的窗体的 ProgID。|

## <a name="see-also"></a>请参阅

[按用法分的特性](attributes-by-usage.md)