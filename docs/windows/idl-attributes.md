---
title: IDL 特性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- IDL attributes
- .idl files, attributes
- IDL files, attributes
- .idl files
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c522c039a0471240ba319561485e8cc7f348aaa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881544"
---
# <a name="idl-attributes"></a>IDL 特性
传统上，维护.idl 文件意味着你必须：  
  
-   熟悉的结构和语法的.idl 文件要能够对其进行修改。  
  
-   依赖于向导，它会让你修改.idl 文件的某些方面。  
  
 现在，你可以修改中使用 Visual c + + IDL 特性的源代码文件中的.idl 文件。 在许多情况下，Visual c + + IDL 特性具有与 MIDL 特性相同的名称。 一个 Visual c + + IDL 特性，MIDL 特性的名称相同时，它意味着，将 Visual c + + 属性放在你的源代码文件将包含其这些 MIDL 特性的.idl 文件中产生。 但是，Visual c + + IDL 特性可能提供 MIDL 特性的所有的功能。  
  
 如果不使用[COM 特性](../windows/com-attributes.md)，IDL 特性使你能够定义接口。 编译源代码时，属性用于定义生成的.idl 文件。 如果使用 ATL 项目中的 COM 特性，某些 IDL 特性，例如**组件类**，会导致代码注入到项目。  
  
 请注意， [idl_quote](../windows/idl-quote.md)允许你使用 Visual c + + 的当前版本中不支持的 MIDL 构造。 这和其他属性类似于[importlib](../windows/importlib.md)和[includelib](../windows/includelib-cpp.md)帮助你使用你当前的 Visual c + + 项目中的现有.idl 文件。  
  
|特性|描述|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|表示一个控件，可以由另一个控件聚合。|  
|[appobject](../windows/appobject.md)|标识为一个应用程序对象，它是一个完整的 EXE 应用程序，与关联和指示不存在的函数和属性组件类全局在此类型库中的组件类。|  
|[async_uuid](../windows/async-uuid.md)|指定指示 MIDL 编译器定义的 COM 接口的同步和异步版本的 UUID。|  
|[bindable](../windows/bindable.md)|指示属性支持数据绑定。|  
|[call_as](../windows/call-as.md)|允许不可远程控制函数映射到远程函数。|  
|[case](../windows/case-cpp.md)|与使用[switch_type](../windows/switch-type.md)联合中的属性。|  
|[coclass](../windows/coclass.md)|位置类到.idl 文件为组件类的定义。|  
|[control](../windows/control.md)|指定的用户定义的类型是一个控件。|  
|[cpp_quote](../windows/cpp-quote.md)|发出指定的字符串，而无需引号字符，到生成的头文件。|  
|[defaultbind](../windows/defaultbind.md)|指示最能代表对象的单个、 可绑定属性。|  
|[defaultcollelem](../windows/defaultcollelem.md)|用于 Visual Basic 代码优化。|  
|[defaultvalue](../windows/defaultvalue.md)|允许类型化的可选参数的默认值的规范。|  
|[default](../windows/default-cpp.md)|指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。|  
|[defaultvtable](../windows/defaultvtable.md)|为控件的默认 vtable 接口中定义一个接口。|  
|[dispinterface](../windows/dispinterface.md)|将一个接口作为调度接口置于 .idl 文件中。|  
|[displaybind](../windows/displaybind.md)|指示应显示给用户作为可绑定的属性。|  
|[dual](../windows/dual.md)|将接口置于.idl 文件中作为双重接口。|  
|[entry](../windows/entry.md)|通过标识 DLL 中的入口点，在模块中指定导出的函数或常量。|  
|[first_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|  
|[helpcontext](../windows/helpcontext.md)|指定允许用户查看有关此帮助文件中的元素信息的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置类型库的帮助文件的名称。|  
|[helpstringcontext](../windows/helpstringcontext.md)|.Hlp 或.chm 文件中指定的帮助主题的 ID。|  
|[helpstringdll](../windows/helpstringdll.md)|指定要用于执行文档字符串查找 （本地化） 的 dll 的名称。|  
|[helpstring](../windows/helpstring.md)|指定用于描述应用于元素的字符字符串。|  
|[hidden](../windows/hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|  
|[idl_module](../windows/idl-module.md)|在 DLL 中指定的入口点。|  
|[idl_quote](../windows/idl-quote.md)|允许你使用属性或 IDL 构造不支持的 Visual c + + 的当前版本。|  
|[id](../windows/id.md)|指定的成员函数 （属性或方法，在接口或调度接口） DISPID。|  
|[iid_is](../windows/iid-is.md)|指定的接口指针指向 COM 接口的 IID。|  
|[immediatebind](../windows/immediatebind.md)|指示数据库将立即收到通知的数据绑定对象的属性的所有更改。|  
|[importlib](../windows/importlib.md)|使已编译到另一个类型库中的类型可供所创建的类型库使用。|  
|[import](../windows/import.md)|指定包含你想要从您的主要.idl 文件引用的定义的另一个.idl、.odl 或标头文件。|  
|[include](../windows/include-cpp.md)|指定要包含在生成的.idl 文件中的一个或多个标头文件。|  
|[includelib](../windows/includelib-cpp.md)|导致要包含在生成的.idl 文件的.idl 或.h 文件。|  
|[in](../windows/in-cpp.md)|指示参数是要调用的过程中传递给调用的过程。|  
|[last_is](../windows/last-is.md)|指定要传输的最后一个数组元素的索引。|  
|[lcid](../windows/lcid.md)|可以将区域设置标识符传递给函数。|  
|[length_is](../windows/length-is.md)|指定要传输的数组元素的数目。|  
|[licensed](../windows/licensed.md)|指示的组件类它所应用于获得了许可证，并且必须使用实例化**IClassFactory2**。|  
|[local](../windows/local-cpp.md)|可用作接口标头中使用时的标头生成器 MIDL 编译器。 当使用单个函数中，指定为其生成没有存根 （stub） 的本地过程。|  
|[max_is](../windows/max-is.md)|指定有效的数组索引的最大值。|  
|[模块](../windows/module-cpp.md)|定义.Idl 文件中的库块。|  
|[ms_union](../windows/ms-union.md)|控制 nonencapsulated 联合的网络数据表示形式对齐方式。|  
|[no_injected_text](../windows/no-injected-text.md)|阻止编译器将注入代码作为特性，请使用结果。|  
|[nonbrowsable](../windows/nonbrowsable.md)|指示接口成员不应显示在属性浏览器中。|  
|[noncreatable](../windows/noncreatable.md)|定义本身不能实例化的对象。|  
|[nonextensible](../windows/nonextensible.md)|指定`IDispatch`实现仅包括的属性和方法的接口描述中列出，并在运行时不能与其他成员扩展。|  
|[object](../windows/object-cpp.md)|标识的自定义接口;自定义特性的同义词。|  
|[odl](../windows/odl.md)|标识为对象描述语言 (ODL) 接口的接口。|  
|[oleautomation](../windows/oleautomation.md)|指示接口是与自动化兼容。|  
|[可选](../windows/optional-cpp.md)|指定的成员函数的可选参数。|  
|[out](../windows/out-cpp.md)|标识从被调用过程返回到调用过程（从服务器到客户端）的指针参数。|  
|[pointer_default](../windows/pointer-default.md)|参数列表中指定除顶级指针显示的所有指针的指针默认属性。|  
|[pragma](../windows/pragma.md)|发出指定的字符串，而无需引号字符，到生成的.idl 文件。|  
|[progid](../windows/progid.md)|指定 COM 对象的 ProgID。|  
|[propget](../windows/propget.md)|指定的属性访问器 (get) 函数。|  
|[propputref](../windows/propputref.md)|指定使用的引用，而不是值的属性设置函数。|  
|[propput](../windows/propput.md)|指定属性设置功能。|  
|[ptr](../windows/ptr.md)|将一个指针指定为完整的指针。|  
|[public](../windows/public-cpp-attributes.md)|可确保即使它未从引用.idl 文件中，typedef 将转到类型库。|  
|[范围](../windows/range-cpp.md)|指定自变量或在运行时设置其值的字段的允许值的范围。|  
|[readonly](../windows/readonly-cpp.md)|禁止对变量赋值。|  
|[ref](../windows/ref-cpp.md)|标识引用指针。|  
|[requestedit](../windows/requestedit.md)|该值指示属性是否支持**OnRequestEdit**通知。|  
|[restricted](../windows/restricted.md)|指定不能任意方式调用库或模块、 接口或调度接口的成员。|  
|[retval](../windows/retval.md)|指定参数，用于接收成员的返回值。|  
|[size_is](../windows/size-is.md)|指定的内存大小为固定大小的指针分配且大小调整了大小的指针和单字节或多维数组的指针。|  
|[源](../windows/source-cpp.md)|指示类、 属性或方法的成员是事件的源。|  
|[string](../windows/string-cpp.md)|指示的一维`char`， `wchar_t`，**字节**，或等效的数组或指向这样的数组的指针都必须视为字符串。|  
|[switch_is](../windows/switch-is.md)|指定的表达式或充当选择联合成员联合判别的标识符。|  
|[switch_type](../windows/switch-type.md)|标识用作联合判别变量的类型。|  
|[transmit_as](../windows/transmit-as.md)|指示编译器将提供的类型，哪些客户端和服务器应用程序操作，与传输类型相关联。|  
|[uidefault](../windows/uidefault.md)|表示类型信息成员以在用户界面中显示的默认成员。|  
|[unique](../windows/unique-cpp.md)|指定一个唯一指针。|  
|[usesgetlasterror](../windows/usesgetlasterror.md)|告知调用方，是否调用该函数时，没有出错，则可以调用调用方`GetLastError`以检索的错误代码。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定为类或接口的唯一 ID。|  
|[v1_enum](../windows/v1-enum.md)|指示指定的枚举的类型可为一个 32 位实体，而不是 16 位默认传输。|  
|[vararg](../windows/vararg.md)|指定该函数采用数目可变的参数。|  
|[vi_progid](../windows/vi-progid.md)|指定独立于版本的窗体的 ProgID。|  
|[wire_marshal](../windows/wire-marshal.md)|指定将用于传输而不是特定于应用程序的数据类型的数据类型。|  
  
## <a name="see-also"></a>请参阅  
 [按组分的特性](../windows/attributes-by-group.md)   
 [特性限制](http://msdn.microsoft.com/en-us/6e6c4329-f667-4869-b991-cbe9cb7a8f61)