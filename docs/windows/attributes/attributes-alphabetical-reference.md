---
title: 按字母顺序的特性参考
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
f1_keywords:
- vc.attributes
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
ms.openlocfilehash: dbbb406765c0664f2cd332524a61713f9c67cf9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167506"
---
# <a name="attributes-alphabetical-reference"></a>按字母顺序的特性参考

Microsoft C++编译器提供以下属性：

|特性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|指示控件可由另一个控件聚合。|
|[aggregates](aggregates.md)|指示控件聚合目标类。|
|[appobject](appobject.md)|将 coclass 标识为与完整 EXE 应用程序关联的应用程序对象，并指示 coclass 的函数和属性在此类型库中全局可用。|
|[async_uuid](async-uuid.md)|指定指示 MIDL 编译器定义 COM 接口的同步和异步版本的 UUID。|
|[attribute](attribute.md)|允许你创建自定义属性。|
|[bindable](bindable.md)|指示该属性支持数据绑定。|
|[call_as](call-as.md)|使不可远程处理函数能够映射到远程函数。|
|[case](case-cpp.md)|与联合中的[switch_type](switch-type.md)特性一起使用。|
|[coclass](coclass.md)|创建可实现 COM 接口的 COM 对象。|
|[com_interface_entry](com-interface-entry-cpp.md)|向 COM 映射添加接口条目。|
|[control](control.md)|指定用户定义类型为控件。|
|[cpp_quote](cpp-quote.md)|向生成的标头文件发出指定的字符串（不含引号字符）。|
|[custom](custom-cpp.md)|允许您定义自己的属性。|
|[db_accessor](db-accessor.md)|绑定行集中的列，并将其绑定到相应的访问器映射。|
|[db_column](db-column.md)|将指定列绑定到行集。|
|[db_command](db-command.md)|执行 OLE DB 命令。|
|[db_param](db-param.md)|将指定的成员变量与输入或输出参数关联。|
|[db_source](db-source.md)|通过提供程序创建和封装到数据源的连接。|
|[db_table](db-table.md)|打开 OLE DB 表。|
|[default](default-cpp.md)|指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。|
|[defaultbind](defaultbind.md)|指示最能表示对象的单个可绑定属性。|
|[defaultcollelem](defaultcollelem.md)|用于 Visual Basic 代码优化。|
|[defaultvalue](defaultvalue.md)|允许为类型化可选参数指定默认值。|
|[defaultvtable](defaultvtable.md)|将接口定义为控件的默认 vtable 接口。|
|[dispinterface](dispinterface.md)|将一个接口作为调度接口置于 .idl 文件中。|
|[displaybind](displaybind.md)|指示应作为可绑定属性显示给用户的属性。|
|[dual](dual.md)|将一个接口作为双重接口放置在 .idl 文件中。|
|[emitidl](emitidl.md)|确定是否将处理所有后续 IDL 特性并将其放置在生成的 .idl 文件中。|
|[entry](entry.md)|通过标识 DLL 中的入口点，在模块中指定导出的函数或常量。|
|[event_receiver](event-receiver.md)|创建事件接收器。|
|[event_source](event-source.md)|创建事件源。|
|[export](export.md)|导致将数据结构放置在 .idl 文件中。|
|[first_is](first-is.md)|指定要传输的第一个数组元素的索引。|
|[helpcontext](helpcontext.md)|指定一个上下文 ID，该 ID 允许用户在帮助文件中查看有关此元素的信息。|
|[helpfile](helpfile.md)|设置类型库的帮助文件的名称。|
|[helpstring](helpstring.md)|指定 .hlp 或 .chm 文件中帮助主题的 ID。|
|[helpstringdll](helpstringdll.md)|指定要用于执行文档字符串查找（本地化）的 DLL 的名称。|
|[hidden](hidden.md)|指示该项存在，但不应在面向用户的浏览器中显示。|
|[id](id.md)|为成员函数（在接口或调度接口中为属性或方法）指定 DISPID。|
|[idl_module](idl-module.md)|指定 DLL 中的入口点。|
|[idl_quote](idl-quote.md)|允许使用当前版本的视觉对象C++不支持的属性或 IDL 构造。|
|[iid_is](iid-is.md)|指定接口指针所指向的 COM 接口的 IID。|
|[immediatebind](immediatebind.md)|指示将立即通知数据库对数据绑定对象的属性所做的所有更改。|
|[implements](implements-cpp.md)|指定强制成为 IDL 组件类成员的调度接口。|
|[implements_category](implements-category.md)|指定类实现的组件类别。|
|[import](import.md)|指定另一个 .idl、odl 或头文件，该文件包含要从您的主 .idl 文件引用的定义。|
|[importidl](importidl.md)|将指定的 .idl 文件插入生成的 .idl 文件。|
|[importlib](importlib.md)|使已编译到另一个类型库中的类型可供所创建的类型库使用。|
|[in](in-cpp.md)|指示参数将从调用过程传递给被调用过程。|
|[include](include-cpp.md)|指定要包含在生成的 .idl 文件中的一个或多个标头文件。|
|[includelib](includelib-cpp.md)|导致在生成的 .idl 文件中包含 .idl 或 .h 文件。|
|[last_is](last-is.md)|指定要传输的最后一个数组元素的索引。|
|[lcid](lcid.md)|使你可以将区域设置标识符传递给函数。|
|[length_is](length-is.md)|指定要传输的数组元素的数目。|
|[library_block](library-block.md)|将构造置于 .idl 文件的库块内。|
|[licensed](licensed.md)|指示它所应用到的 coclass 已获得许可，必须使用 `IClassFactory2`进行实例化。|
|[local](local-cpp.md)|允许在接口标头中使用 MIDL 编译器时将其用作标头生成器。 在单独的函数中使用时，指定不会为其生成存根的本地过程。|
|[max_is](max-is.md)|指定有效数组索引的最大值。|
|[module](module-cpp.md)|定义.Idl 文件中的库块。|
|[ms_union](ms-union.md)|控制 nonencapsulated 联合的网络数据表示形式的对齐方式。|
|[no_injected_text](no-injected-text.md)|阻止编译器将代码注入到属性使用的结果中。|
|[nonbrowsable](nonbrowsable.md)|指示不应在属性浏览器中显示接口成员。|
|[noncreatable](noncreatable.md)|定义一个对象，该对象不能单独实例化。|
|[nonextensible](nonextensible.md)|指定 `IDispatch` 实现仅包含接口说明中列出的属性和方法，而不能在运行时与其他成员一起扩展。|
|[object](object-cpp.md)|标识自定义接口;与自定义属性同义。|
|[odl](odl.md)|将接口标识为对象描述语言（ODL）接口。|
|[oleautomation](oleautomation.md)|指示接口与自动化兼容。|
|[optional](optional-cpp.md)|为成员函数指定一个可选参数。|
|[out](out-cpp.md)|标识从被调用过程返回到调用过程（从服务器到客户端）的指针参数。|
|[pointer_default](pointer-default.md)|为除 "参数列表" 中显示的顶级指针之外的所有指针指定默认指针特性。|
|[pragma](pragma.md)|向生成的 .idl 文件发出指定的字符串（不含引号字符）。|
|[progid](progid.md)|指定 COM 对象的 ProgID。|
|[propget](propget.md)|指定属性访问器（get）函数。|
|[propput](propput.md)|指定属性设置功能。|
|[propputref](propputref.md)|指定使用引用而不是值的属性设置函数。|
|[ptr](ptr.md)|将指针指定为完全指针。|
|[public](public-cpp-attributes.md)|确保 typedef 将进入类型库，即使它未从 .idl 文件中引用。|
|[range](range-cpp.md)|为其值在运行时设置的参数或字段指定一系列允许的值。|
|[rdx](rdx.md)|创建或修改注册表项。|
|[readonly](readonly-cpp.md)|禁止对变量赋值。|
|[ref](ref-cpp.md)|标识引用指针。|
|[registration_script](registration-script.md)|执行指定的注册脚本。|
|[requestedit](requestedit.md)|指示该属性支持 `OnRequestEdit` 通知。|
|[requires_category](requires-category.md)|指定类所需的组件类别。|
|[restricted](restricted.md)|指定不能任意调用某个库或模块、接口或调度接口的成员。|
|[retval](retval.md)|指定接收该成员的返回值的参数。|
|[satype](satype.md)|指定 `SAFEARRAY`的数据类型。|
|[size_is](size-is.md)|指定分配给大小指针的内存大小、大小指针的大小指针以及单数组或多维数组。|
|[source](source-cpp.md)|指示类、属性或方法的成员是事件的源。|
|[string](string-cpp.md)|指示必须将一维**char**、 **wchar_t**、`byte`或等效数组或指向此类数组的指针视为字符串。|
|[support_error_info](support-error-info.md)|支持对目标对象进行错误报告。|
|[switch_is](switch-is.md)|指定充当用于选择联合成员的联合判别的表达式或标识符。|
|[switch_type](switch-type.md)|标识用作联合判别的变量的类型。|
|[synchronize](synchronize.md)|同步对方法的访问。|
|[threading](threading-cpp.md)|指定 COM 对象的线程模型。|
|[transmit_as](transmit-as.md)|指示编译器将客户端和服务器应用程序操作的显示类型与传输类型相关联。|
|[uidefault](uidefault.md)|指示类型信息成员是在用户界面中显示的默认成员。|
|[unique](unique-cpp.md)|指定唯一的指针。|
|[usesgetlasterror](usesgetlasterror.md)|告诉调用方如果在调用该函数时出现错误，则调用方可以调用 `GetLastError` 来检索错误代码。|
|[uuid](uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|
|[v1_enum](v1-enum.md)|指示指定的枚举类型传输为32位实体，而不是16位默认值。|
|[vararg](vararg.md)|指定该函数采用可变数量的参数。|
|[版本](version-cpp.md)|标识接口或类的多个版本中的特定版本。|
|[vi_progid](vi-progid.md)|指定 ProgID 的与版本无关的形式。|
|[wire_marshal](wire-marshal.md)|指定将用于传输的数据类型，而不是特定于应用程序的数据类型。|

## <a name="see-also"></a>请参阅

[COM 和 .NET 的 C++ 属性](cpp-attributes-com-net.md)<br/>
[按组分的特性](attributes-by-group.md)<br/>
[按用法分的特性](attributes-by-usage.md)
