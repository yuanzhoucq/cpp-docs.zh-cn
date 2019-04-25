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
ms.openlocfilehash: 386afe5362f876cd1489a35839f4f8cfc2381e91
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148492"
---
# <a name="attributes-alphabetical-reference"></a>按字母顺序的特性参考

以下属性可在 microsoftC++编译器：

|特性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示一个控件，可以聚合由另一个控件。|
|[aggregates](aggregates.md)|指示控件聚合的目标类。|
|[appobject](appobject.md)|标识作为应用程序对象，这是一个完整的 EXE 应用程序，与相关联，表示在函数和属性组件类的全局范围内使用此类型库中的组件类。|
|[async_uuid](async-uuid.md)|指定指示 MIDL 编译器定义的 COM 接口的同步和异步版本的 UUID。|
|[attribute](attribute.md)|可以创建自定义属性。|
|[bindable](bindable.md)|指示该属性支持数据绑定。|
|[call_as](call-as.md)|允许不可远程处理函数映射到远程函数。|
|[case](case-cpp.md)|用于[switch_type](switch-type.md)联合中的属性。|
|[coclass](coclass.md)|创建 COM 对象，可以实现 COM 接口。|
|[com_interface_entry](com-interface-entry-cpp.md)|将接口条目添加到 COM 映射。|
|[control](control.md)|指定用户定义类型为控件。|
|[cpp_quote](cpp-quote.md)|将指定的字符串，而无需引号字符，发送到生成的头文件。|
|[custom](custom-cpp.md)|可以定义自己的属性。|
|[db_accessor](db-accessor.md)|绑定行集中的列，并将它们绑定到相应的访问器映射。|
|[db_column](db-column.md)|将指定的列绑定到行集。|
|[db_command](db-command.md)|执行 OLE DB 命令。|
|[db_param](db-param.md)|将指定的成员变量与输入或输出参数相关联。|
|[db_source](db-source.md)|创建并封装到数据源的提供程序通过建立的连接。|
|[db_table](db-table.md)|将打开一个 OLE DB 表。|
|[default](default-cpp.md)|指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。|
|[defaultbind](defaultbind.md)|指示最能代表对象的单个、 可绑定属性。|
|[defaultcollelem](defaultcollelem.md)|用于 Visual Basic 代码优化。|
|[defaultvalue](defaultvalue.md)|允许类型化可选参数的默认值的规范。|
|[defaultvtable](defaultvtable.md)|为控件的默认 vtable 接口定义的接口。|
|[dispinterface](dispinterface.md)|将一个接口作为调度接口置于 .idl 文件中。|
|[displaybind](displaybind.md)|指示应显示给用户作为可绑定的属性。|
|[dual](dual.md)|双重接口.idl 文件中放置一个接口。|
|[emitidl](emitidl.md)|确定是否将处理并放置在生成的.idl 文件中所有后续的 IDL 特性。|
|[entry](entry.md)|通过标识 DLL 中的入口点，在模块中指定的导出的函数或常量。|
|[event_receiver](event-receiver.md)|创建事件接收器。|
|[event_source](event-source.md)|创建事件源。|
|[export](export.md)|导致要放置在.idl 文件中的数据结构。|
|[first_is](first-is.md)|指定要传输的第一个数组元素的索引。|
|[helpcontext](helpcontext.md)|指定允许用户查看有关此帮助文件中的元素的信息的上下文 ID。|
|[helpfile](helpfile.md)|设置类型库的帮助文件的名称。|
|[helpstring](helpstring.md)|在.hlp 或.chm 文件中指定的帮助主题的 ID。|
|[helpstringdll](helpstringdll.md)|指定要用于执行文档字符串查找 （本地化） DLL 的名称。|
|[hidden](hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|
|[id](id.md)|指定的成员函数 （属性或方法，请在接口或调度接口） 的 DISPID。|
|[idl_module](idl-module.md)|在 DLL 中指定的入口点。|
|[idl_quote](idl-quote.md)|可以使用属性或视觉对象的当前版本中不支持的 IDL 构造C++。|
|[iid_is](iid-is.md)|指定的接口指针指向了 COM 接口的 IID。|
|[immediatebind](immediatebind.md)|指示数据库将立即收到通知的所有更改将数据绑定对象的属性。|
|[implements](implements-cpp.md)|指定强制 IDL 组件类的成员的调度接口。|
|[implements_category](implements-category.md)|指定类的实现的组件类别。|
|[import](import.md)|指定包含你想要从主.idl 文件中引用的定义的另一个.idl、.odl 或标头文件。|
|[importidl](importidl.md)|将指定的.idl 文件插入到生成的.idl 文件。|
|[importlib](importlib.md)|使已编译到另一个类型库中的类型可供所创建的类型库使用。|
|[in](in-cpp.md)|指示参数是要从调用过程传递给被调用过程。|
|[include](include-cpp.md)|指定要包括在生成的.idl 文件中的一个或多个标头文件。|
|[includelib](includelib-cpp.md)|导致要生成的.idl 文件中包含的.idl 或.h 文件。|
|[last_is](last-is.md)|指定要传输的最后一个数组元素的索引。|
|[lcid](lcid.md)|可以将区域设置标识符传递给函数。|
|[length_is](length-is.md)|指定要传输的数组元素数。|
|[library_block](library-block.md)|将放置在.idl 文件的库块中的构造。|
|[licensed](licensed.md)|指示它所应用于的组件类授予许可，并且必须使用实例化`IClassFactory2`。|
|[local](local-cpp.md)|可以使用 MIDL 编译器为标头生成器界面标头中使用时。 单个函数中使用时，将指定为其生成无存根 （stub） 的本地过程。|
|[max_is](max-is.md)|指定有效的数组索引的最大值。|
|[module](module-cpp.md)|定义.Idl 文件中的库块。|
|[ms_union](ms-union.md)|控制 nonencapsulated 联合的网络数据表示形式对齐方式。|
|[no_injected_text](no-injected-text.md)|禁止编译器注入代码作为特性使用结果。|
|[nonbrowsable](nonbrowsable.md)|指示接口成员不应显示在属性浏览器中。|
|[noncreatable](noncreatable.md)|定义不能实例化本身的对象。|
|[nonextensible](nonextensible.md)|指定`IDispatch`实现仅包括属性和方法的接口描述中列出，并在运行时不能与其他成员扩展。|
|[object](object-cpp.md)|标识的自定义的接口;自定义特性的代名词。|
|[odl](odl.md)|标识为对象描述语言 (ODL) 接口的接口。|
|[oleautomation](oleautomation.md)|指示接口使用自动化兼容。|
|[optional](optional-cpp.md)|指定的成员函数的可选参数。|
|[out](out-cpp.md)|标识从被调用过程返回到调用过程（从服务器到客户端）的指针参数。|
|[pointer_default](pointer-default.md)|在参数列表中指定除顶级指针显示的所有指针的默认指针特性。|
|[pragma](pragma.md)|将指定的字符串，而无需引号字符，发送到生成的.idl 文件。|
|[progid](progid.md)|指定 COM 对象的 ProgID。|
|[propget](propget.md)|指定的属性访问器 (get) 函数。|
|[propput](propput.md)|指定属性设置功能。|
|[propputref](propputref.md)|指定使用引用而不是值的属性设置函数。|
|[ptr](ptr.md)|将一个指针，指定为完整的指针。|
|[public](public-cpp-attributes.md)|可确保即使它未从引用的.idl 文件中，一个 typedef 将转到类型库。|
|[range](range-cpp.md)|指定参数或在运行时设置其值的字段的允许值的范围。|
|[rdx](rdx.md)|创建或修改注册表项。|
|[readonly](readonly-cpp.md)|禁止分配给一个变量。|
|[ref](ref-cpp.md)|标识引用指针。|
|[registration_script](registration-script.md)|执行指定的注册脚本。|
|[requestedit](requestedit.md)|指示该属性支持 `OnRequestEdit` 通知。|
|[requires_category](requires-category.md)|指定所需的组件类别的类。|
|[restricted](restricted.md)|指定的库或模块、 接口或调度接口的成员不能任意调用。|
|[retval](retval.md)|指定接收该成员的返回值的参数。|
|[satype](satype.md)|指定的数据类型`SAFEARRAY`。|
|[size_is](size-is.md)|指定的内存大小为固定大小的指针分配、 调整大小的指针和单字节或多维数组的指针。|
|[source](source-cpp.md)|指示类、 属性或方法的一个成员是事件的源。|
|[string](string-cpp.md)|指示的一维**char**， **wchar_t**， `byte`，或等效的数组或指针，指向此类必须视为字符串。|
|[support_error_info](support-error-info.md)|支持的错误报告目标对象。|
|[switch_is](switch-is.md)|指定的表达式或作为联合判别选择联合成员的标识符。|
|[switch_type](switch-type.md)|标识用作联合判别变量的类型。|
|[synchronize](synchronize.md)|同步访问的方法。|
|[threading](threading-cpp.md)|指定 COM 对象的线程处理模型。|
|[transmit_as](transmit-as.md)|指示编译器将提供的类型，哪些客户端和服务器应用程序操作，与传输类型相关联。|
|[uidefault](uidefault.md)|指示该类型信息成员是用户界面中显示的默认成员。|
|[unique](unique-cpp.md)|指定一个唯一指针。|
|[usesgetlasterror](usesgetlasterror.md)|告知调用方，是否调用该函数时出现错误，然后可以调用调用方`GetLastError`检索错误代码。|
|[uuid](uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|
|[v1_enum](v1-enum.md)|指示指定的枚举的类型作为一个 32 位实体，而不是 16 位默认传输。|
|[vararg](vararg.md)|指定该函数采用数量可变的参数。|
|[版本](version-cpp.md)|标识的接口或类的多个版本间的特定版本。|
|[vi_progid](vi-progid.md)|指定独立于版本的窗体的 ProgID。|
|[wire_marshal](wire-marshal.md)|指定将用于传输而不是特定于应用程序的数据类型的数据类型。|

## <a name="see-also"></a>请参阅

[COM 和 .NET 的 C++ 属性](cpp-attributes-com-net.md)<br/>
[按组分的特性](attributes-by-group.md)<br/>
[按用法分的特性](attributes-by-usage.md)