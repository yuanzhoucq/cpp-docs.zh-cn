---
title: 属性按字母顺序参考 |Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.attributes
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1203c871b67c8bd87faef92c840c6236fb028cd3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595803"
---
# <a name="attributes-alphabetical-reference"></a>按字母顺序的特性参考

Visual c + + 中提供了以下属性。

|特性|描述|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|表示一个控件，可以聚合由另一个控件。|
|[aggregates](../windows/aggregates.md)|指示控件聚合的目标类。|
|[appobject](../windows/appobject.md)|标识作为应用程序对象，这是一个完整的 EXE 应用程序，与相关联，表示在函数和属性组件类的全局范围内使用此类型库中的组件类。|
|[async_uuid](../windows/async-uuid.md)|指定指示 MIDL 编译器定义的 COM 接口的同步和异步版本的 UUID。|
|[attribute](../windows/attribute.md)|可以创建自定义属性。|
|[bindable](../windows/bindable.md)|指示该属性支持数据绑定。|
|[call_as](../windows/call-as.md)|允许不可远程处理函数映射到远程函数。|
|[case](../windows/case-cpp.md)|用于[switch_type](../windows/switch-type.md)联合中的属性。|
|[coclass](../windows/coclass.md)|创建 COM 对象，可以实现 COM 接口。|
|[com_interface_entry](../windows/com-interface-entry-cpp.md)|将接口条目添加到 COM 映射。|
|[control](../windows/control.md)|指定用户定义类型为控件。|
|[cpp_quote](../windows/cpp-quote.md)|将指定的字符串，而无需引号字符，发送到生成的头文件。|
|[custom](../windows/custom-cpp.md)|可以定义自己的属性。|
|[db_accessor](../windows/db-accessor.md)|绑定行集中的列，并将它们绑定到相应的访问器映射。|
|[db_column](../windows/db-column.md)|将指定的列绑定到行集。|
|[db_command](../windows/db-command.md)|执行 OLE DB 命令。|
|[db_param](../windows/db-param.md)|将指定的成员变量与输入或输出参数相关联。|
|[db_source](../windows/db-source.md)|创建并封装到数据源的提供程序通过建立的连接。|
|[db_table](../windows/db-table.md)|将打开一个 OLE DB 表。|
|[default](../windows/default-cpp.md)|指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。|
|[defaultbind](../windows/defaultbind.md)|指示最能代表对象的单个、 可绑定属性。|
|[defaultcollelem](../windows/defaultcollelem.md)|用于 Visual Basic 代码优化。|
|[defaultvalue](../windows/defaultvalue.md)|允许类型化可选参数的默认值的规范。|
|[defaultvtable](../windows/defaultvtable.md)|为控件的默认 vtable 接口定义的接口。|
|[dispinterface](../windows/dispinterface.md)|将一个接口作为调度接口置于 .idl 文件中。|
|[displaybind](../windows/displaybind.md)|指示应显示给用户作为可绑定的属性。|
|[dual](../windows/dual.md)|双重接口.idl 文件中放置一个接口。|
|[emitidl](../windows/emitidl.md)|确定是否将处理并放置在生成的.idl 文件中所有后续的 IDL 特性。|
|[entry](../windows/entry.md)|通过标识 DLL 中的入口点，在模块中指定的导出的函数或常量。|
|[event_receiver](../windows/event-receiver.md)|创建事件接收器。|
|[event_source](../windows/event-source.md)|创建事件源。|
|[export](../windows/export.md)|导致要放置在.idl 文件中的数据结构。|
|[first_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|
|[helpcontext](../windows/helpcontext.md)|指定允许用户查看有关此帮助文件中的元素的信息的上下文 ID。|
|[helpfile](../windows/helpfile.md)|设置类型库的帮助文件的名称。|
|[helpstring](../windows/helpstring.md)|在.hlp 或.chm 文件中指定的帮助主题的 ID。|
|[helpstringdll](../windows/helpstringdll.md)|指定要用于执行文档字符串查找 （本地化） DLL 的名称。|
|[hidden](../windows/hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|
|[id](../windows/id.md)|指定的成员函数 （属性或方法，请在接口或调度接口） 的 DISPID。|
|[idl_module](../windows/idl-module.md)|在 DLL 中指定的入口点。|
|[idl_quote](../windows/idl-quote.md)|允许你使用属性或 IDL 构造不支持当前版本的 Visual c + + 中的。|
|[iid_is](../windows/iid-is.md)|指定的接口指针指向了 COM 接口的 IID。|
|[immediatebind](../windows/immediatebind.md)|指示数据库将立即收到通知的所有更改将数据绑定对象的属性。|
|[实现](../windows/implements-cpp.md)|指定强制 IDL 组件类的成员的调度接口。|
|[implements_category](../windows/implements-category.md)|指定类的实现的组件类别。|
|[import](../windows/import.md)|指定包含你想要从主.idl 文件中引用的定义的另一个.idl、.odl 或标头文件。|
|[importidl](../windows/importidl.md)|将指定的.idl 文件插入到生成的.idl 文件。|
|[importlib](../windows/importlib.md)|使已编译到另一个类型库中的类型可供所创建的类型库使用。|
|[in](../windows/in-cpp.md)|指示参数是要从调用过程传递给被调用过程。|
|[include](../windows/include-cpp.md)|指定要包括在生成的.idl 文件中的一个或多个标头文件。|
|[includelib](../windows/includelib-cpp.md)|导致要生成的.idl 文件中包含的.idl 或.h 文件。|
|[last_is](../windows/last-is.md)|指定要传输的最后一个数组元素的索引。|
|[lcid](../windows/lcid.md)|可以将区域设置标识符传递给函数。|
|[length_is](../windows/length-is.md)|指定要传输的数组元素数。|
|[library_block](../windows/library-block.md)|将放置在.idl 文件的库块中的构造。|
|[licensed](../windows/licensed.md)|指示它所应用于的组件类授予许可，并且必须使用实例化`IClassFactory2`。|
|[local](../windows/local-cpp.md)|可以使用 MIDL 编译器为标头生成器界面标头中使用时。 单个函数中使用时，将指定为其生成无存根 （stub） 的本地过程。|
|[max_is](../windows/max-is.md)|指定有效的数组索引的最大值。|
|[模块](../windows/module-cpp.md)|定义.Idl 文件中的库块。|
|[ms_union](../windows/ms-union.md)|控制 nonencapsulated 联合的网络数据表示形式对齐方式。|
|[no_injected_text](../windows/no-injected-text.md)|禁止编译器注入代码作为特性使用结果。|
|[nonbrowsable](../windows/nonbrowsable.md)|指示接口成员不应显示在属性浏览器中。|
|[noncreatable](../windows/noncreatable.md)|定义不能实例化本身的对象。|
|[nonextensible](../windows/nonextensible.md)|指定`IDispatch`实现仅包括属性和方法的接口描述中列出，并在运行时不能与其他成员扩展。|
|[object](../windows/object-cpp.md)|标识的自定义的接口;自定义特性的代名词。|
|[odl](../windows/odl.md)|标识为对象描述语言 (ODL) 接口的接口。|
|[oleautomation](../windows/oleautomation.md)|指示接口使用自动化兼容。|
|[可选](../windows/optional-cpp.md)|指定的成员函数的可选参数。|
|[out](../windows/out-cpp.md)|标识从被调用过程返回到调用过程（从服务器到客户端）的指针参数。|
|[pointer_default](../windows/pointer-default.md)|在参数列表中指定除顶级指针显示的所有指针的默认指针特性。|
|[pragma](../windows/pragma.md)|将指定的字符串，而无需引号字符，发送到生成的.idl 文件。|
|[progid](../windows/progid.md)|指定 COM 对象的 ProgID。|
|[propget](../windows/propget.md)|指定的属性访问器 (get) 函数。|
|[propput](../windows/propput.md)|指定属性设置功能。|
|[propputref](../windows/propputref.md)|指定使用引用而不是值的属性设置函数。|
|[ptr](../windows/ptr.md)|将一个指针，指定为完整的指针。|
|[public](../windows/public-cpp-attributes.md)|可确保即使它未从引用的.idl 文件中，一个 typedef 将转到类型库。|
|[范围](../windows/range-cpp.md)|指定参数或在运行时设置其值的字段的允许值的范围。|
|[rdx](../windows/rdx.md)|创建或修改注册表项。|
|[readonly](../windows/readonly-cpp.md)|禁止分配给一个变量。|
|[ref](../windows/ref-cpp.md)|标识引用指针。|
|[registration_script](../windows/registration-script.md)|执行指定的注册脚本。|
|[requestedit](../windows/requestedit.md)|指示该属性支持`OnRequestEdit`通知。|
|[requires_category](../windows/requires-category.md)|指定所需的组件类别的类。|
|[restricted](../windows/restricted.md)|指定的库或模块、 接口或调度接口的成员不能任意调用。|
|[retval](../windows/retval.md)|指定接收该成员的返回值的参数。|
|[satype](../windows/satype.md)|指定的数据类型`SAFEARRAY`。|
|[size_is](../windows/size-is.md)|指定的内存大小为固定大小的指针分配、 调整大小的指针和单字节或多维数组的指针。|
|[source](../windows/source-cpp.md)|指示类、 属性或方法的一个成员是事件的源。|
|[string](../windows/string-cpp.md)|指示的一维**char**， **wchar_t**， `byte`，或等效的数组或指针，指向此类必须视为字符串。|
|[support_error_info](../windows/support-error-info.md)|支持的错误报告目标对象。|
|[switch_is](../windows/switch-is.md)|指定的表达式或作为联合判别选择联合成员的标识符。|
|[switch_type](../windows/switch-type.md)|标识用作联合判别变量的类型。|
|[synchronize](../windows/synchronize.md)|同步访问的方法。|
|[线程处理](../windows/threading-cpp.md)|指定 COM 对象的线程处理模型。|
|[transmit_as](../windows/transmit-as.md)|指示编译器将提供的类型，哪些客户端和服务器应用程序操作，与传输类型相关联。|
|[uidefault](../windows/uidefault.md)|指示该类型信息成员是用户界面中显示的默认成员。|
|[unique](../windows/unique-cpp.md)|指定一个唯一指针。|
|[usesgetlasterror](../windows/usesgetlasterror.md)|告知调用方，是否调用该函数时出现错误，然后可以调用调用方`GetLastError`检索错误代码。|
|[uuid](../windows/uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|
|[v1_enum](../windows/v1-enum.md)|指示指定的枚举的类型作为一个 32 位实体，而不是 16 位默认传输。|
|[vararg](../windows/vararg.md)|指定该函数采用数量可变的参数。|
|[version](../windows/version-cpp.md)|标识的接口或类的多个版本间的特定版本。|
|[vi_progid](../windows/vi-progid.md)|指定独立于版本的窗体的 ProgID。|
|[wire_marshal](../windows/wire-marshal.md)|指定将用于传输而不是特定于应用程序的数据类型的数据类型。|

## <a name="see-also"></a>请参阅

[C++ 特性参考](../windows/cpp-attributes-reference.md)  
[概念](../windows/attributed-programming-concepts.md)  
[按组分的特性](../windows/attributes-by-group.md)  
[按用法分的特性](../windows/attributes-by-usage.md)