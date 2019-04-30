---
title: IDL 特性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- IDL attributes
- .idl files [C++], attributes
- IDL files [C++], attributes
- .idl files [C++]
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
ms.openlocfilehash: a699e327eec056bbb36747840990bb9c7ccc259b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409546"
---
# <a name="idl-attributes"></a>IDL 特性

一直以来，维护.idl 文件意味着，您必须为：

- 已经熟悉的结构和语法的.idl 文件以便能够对其进行修改。

- 依赖于一个向导，将让你可以修改.idl 文件的某些方面。

现在，可以修改中使用视觉对象的源代码文件中的.idl 文件C++IDL 特性。 在许多情况下，视觉对象C++IDL 特性具有与 MIDL 属性相同的名称。 当视觉对象的名称C++IDL 属性及其 MIDL 属性相同，这意味着将视觉对象C++源代码文件中的属性将导致.idl 文件包含其作用 MIDL 特性。 但是，视觉对象C++IDL 特性可能无法提供的 MIDL 特性的所有功能。

如果不使用与[COM 特性](com-attributes.md)，IDL 属性，您可以定义接口。 编译的源代码时，这些属性用于定义生成的.idl 文件。 与 COM 特性的 ATL 项目中使用时，一些 IDL 特性，例如`coclass`，会导致代码注入到项目。

请注意， [idl_quote](idl-quote.md)可让你使用不支持当前版本的视觉对象中的 MIDL 构造C++。 这和其他属性，如[importlib](importlib.md)并[includelib](includelib-cpp.md)帮助你使用你当前的视觉对象中的现有.idl 文件C++项目。

|特性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示一个控件，可以聚合由另一个控件。|
|[appobject](appobject.md)|标识作为应用程序对象，这是一个完整的 EXE 应用程序，与相关联，表示在函数和属性组件类的全局范围内使用此类型库中的组件类。|
|[async_uuid](async-uuid.md)|指定指示 MIDL 编译器定义的 COM 接口的同步和异步版本的 UUID。|
|[bindable](bindable.md)|指示该属性支持数据绑定。|
|[call_as](call-as.md)|允许不可远程处理函数映射到远程函数。|
|[case](case-cpp.md)|用于[switch_type](switch-type.md)联合中的属性。|
|[coclass](coclass.md)|位置类到.idl 文件中为组件类的定义。|
|[control](control.md)|指定用户定义类型为控件。|
|[cpp_quote](cpp-quote.md)|将指定的字符串，而无需引号字符，发送到生成的头文件。|
|[defaultbind](defaultbind.md)|指示最能代表对象的单个、 可绑定属性。|
|[defaultcollelem](defaultcollelem.md)|用于 Visual Basic 代码优化。|
|[defaultvalue](defaultvalue.md)|允许类型化可选参数的默认值的规范。|
|[default](default-cpp.md)|指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。|
|[defaultvtable](defaultvtable.md)|为控件的默认 vtable 接口定义的接口。|
|[dispinterface](dispinterface.md)|将一个接口作为调度接口置于 .idl 文件中。|
|[displaybind](displaybind.md)|指示应显示给用户作为可绑定的属性。|
|[dual](dual.md)|双重接口.idl 文件中放置一个接口。|
|[entry](entry.md)|通过标识 DLL 中的入口点，在模块中指定的导出的函数或常量。|
|[first_is](first-is.md)|指定要传输的第一个数组元素的索引。|
|[helpcontext](helpcontext.md)|指定允许用户查看有关此帮助文件中的元素的信息的上下文 ID。|
|[helpfile](helpfile.md)|设置类型库的帮助文件的名称。|
|[helpstringcontext](helpstringcontext.md)|在.hlp 或.chm 文件中指定的帮助主题的 ID。|
|[helpstringdll](helpstringdll.md)|指定要用于执行文档字符串查找 （本地化） DLL 的名称。|
|[helpstring](helpstring.md)|指定一个字符串，用于描述应用该字符串的元素。|
|[hidden](hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|
|[idl_module](idl-module.md)|在 DLL 中指定的入口点。|
|[idl_quote](idl-quote.md)|可以使用属性或视觉对象的当前版本中不支持的 IDL 构造C++。|
|[id](id.md)|指定的成员函数 （属性或方法，请在接口或调度接口） 的 DISPID。|
|[iid_is](iid-is.md)|指定的接口指针指向了 COM 接口的 IID。|
|[immediatebind](immediatebind.md)|指示数据库将立即收到通知的所有更改将数据绑定对象的属性。|
|[importlib](importlib.md)|使已编译到另一个类型库中的类型可供所创建的类型库使用。|
|[import](import.md)|指定包含你想要从主.idl 文件中引用的定义的另一个.idl、.odl 或标头文件。|
|[include](include-cpp.md)|指定要包括在生成的.idl 文件中的一个或多个标头文件。|
|[includelib](includelib-cpp.md)|导致要生成的.idl 文件中包含的.idl 或.h 文件。|
|[in](in-cpp.md)|指示参数是要从调用过程传递给被调用过程。|
|[last_is](last-is.md)|指定要传输的最后一个数组元素的索引。|
|[lcid](lcid.md)|可以将区域设置标识符传递给函数。|
|[length_is](length-is.md)|指定要传输的数组元素数。|
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
|[propputref](propputref.md)|指定使用引用而不是值的属性设置函数。|
|[propput](propput.md)|指定属性设置功能。|
|[ptr](ptr.md)|将一个指针，指定为完整的指针。|
|[public](public-cpp-attributes.md)|可确保即使它未从引用的.idl 文件中，一个 typedef 将转到类型库。|
|[range](range-cpp.md)|指定参数或在运行时设置其值的字段的允许值的范围。|
|[readonly](readonly-cpp.md)|禁止分配给一个变量。|
|[ref](ref-cpp.md)|标识引用指针。|
|[requestedit](requestedit.md)|指示该属性支持 `OnRequestEdit` 通知。|
|[restricted](restricted.md)|指定的库或模块、 接口或调度接口的成员不能任意调用。|
|[retval](retval.md)|指定接收该成员的返回值的参数。|
|[size_is](size-is.md)|指定的内存大小为固定大小的指针分配、 调整大小的指针和单字节或多维数组的指针。|
|[source](source-cpp.md)|指示类、 属性或方法的一个成员是事件的源。|
|[string](string-cpp.md)|指示的一维**char**， **wchar_t**， `byte`，或等效的数组或指针，指向此类必须视为字符串。|
|[switch_is](switch-is.md)|指定的表达式或作为联合判别选择联合成员的标识符。|
|[switch_type](switch-type.md)|标识用作联合判别变量的类型。|
|[transmit_as](transmit-as.md)|指示编译器将提供的类型，哪些客户端和服务器应用程序操作，与传输类型相关联。|
|[uidefault](uidefault.md)|指示该类型信息成员是用户界面中显示的默认成员。|
|[unique](unique-cpp.md)|指定一个唯一指针。|
|[usesgetlasterror](usesgetlasterror.md)|告知调用方，是否调用该函数时出现错误，然后可以调用调用方`GetLastError`检索错误代码。|
|[uuid](uuid-cpp-attributes.md)|指定类或接口的唯一 ID。|
|[v1_enum](v1-enum.md)|指示指定的枚举的类型作为一个 32 位实体，而不是 16 位默认传输。|
|[vararg](vararg.md)|指定该函数采用数量可变的参数。|
|[vi_progid](vi-progid.md)|指定独立于版本的窗体的 ProgID。|
|[wire_marshal](wire-marshal.md)|指定将用于传输而不是特定于应用程序的数据类型的数据类型。|

## <a name="see-also"></a>请参阅

[按组分的特性](attributes-by-group.md)
