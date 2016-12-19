---
title: "IDL Attributes | Microsoft Docs"
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
  - "attributes [C++], reference topics"
  - "IDL attributes"
  - ".idl files, attributes"
  - "IDL files, attributes"
  - ".idl files"
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDL Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

传统上，保留 .idl 文件意味着您必须:  
  
-   熟悉 .idl 文件的结构和语法可以修改它。  
  
-   由向导，会允许您修改 .idl 文件中的某些方面。  
  
 现在，使用 Visual C\+\+ IDL 特性，可以修改 .idl 文件从源代码文件内。  在许多情况下， Visual C\+\+ IDL 特性的名称和 MIDL 属性相同。  在 Visual C\+\+ IDL 特性的名称和 MIDL 属性相同时，这意味着将 Visual C\+\+ 特性在源代码文件以包含其部件 MIDL 属性的 .idl 文件。  但是， Visual C\+\+ IDL 特性可能无法提供 MIDL 属性的所有功能。  
  
 当未使用 [COM 属性](../windows/com-attributes.md)， IDL 特性允许您为接口。  当源代码编译时，属性用于定义生成的 .idl 文件。  当使用与 COM 属性在 ATL 项目，某些 IDL 特性，如 **coclass**，将插入的原因代码添加到项目。  
  
 请注意 [idl\_quote](../windows/idl-quote.md) 可以使用在 Visual C\+\+ 的当前版本不支持的 MIDL 构造。  这和其他属性 \(例如 [importlib](../windows/importlib.md) 和 [includelib](../windows/includelib-cpp.md) 帮助使用现有的 .idl 文件中您将在此 Visual C\+\+ 项目。  
  
|特性|说明|  
|--------|--------|  
|[可聚集的](../windows/aggregatable.md)|指示控件可由另一个复合控件。|  
|[appobject](../windows/appobject.md)|标识 coclass 为应用程序对象，与完整的 EXE 应用程序，并指示 coclass 的功能和特性是全局可用此类型库。|  
|[async\_uuid](../windows/async-uuid.md)|指定处理 MIDL 编译器定义 COM 接口的同步和异步版本的 UUID。|  
|[bindable](../windows/bindable.md)|指示属性支持数据绑定。|  
|[call\_as](../windows/call-as.md)|使一个不可远程控制的函数映射到远程功能。|  
|[case](../windows/case-cpp.md)|使用 [switch\_type](../windows/switch-type.md) 属性在联合。|  
|[coclass](../windows/coclass.md)|将类定义加到 .idl 文件作为 coclass。|  
|[控件](../windows/control.md)|指定用户定义的类型是控件。|  
|[cpp\_quote](../windows/cpp-quote.md)|发出该指定字符串，因此，不带引号字符，以生成的头文件。|  
|[defaultbind](../windows/defaultbind.md)|指示最好地表示对象的唯一，可绑定属性。|  
|[defaultcollelem](../windows/defaultcollelem.md)|用于 Visual Basic 代码优化。|  
|[defaultvalue](../windows/defaultvalue.md)|允许默认的规范一个类型化可选参数的。|  
|[default](../windows/default-cpp.md)|指示在或调度接口中定义的自定义 coclass 表示默认可编程接口。|  
|[defaultvtable](../windows/defaultvtable.md)|定义一个接口作为控件的默认 vtable 接口。|  
|[dispinterface](../windows/dispinterface.md)|在 .idl 文件中放置一个接口作为调度接口。|  
|[displaybind](../windows/displaybind.md)|指示应向用户显示为可绑定的属性。|  
|[dual](../windows/dual.md)|在 .idl 文件中放置一个接口该接口。|  
|[项](../windows/entry.md)|指定一个导出函数或在一个模块的常数传递标识在 DLL 入口点。|  
|[first\_is](../windows/first-is.md)|指定要传输的第一个数组元素的索引。|  
|[helpcontext](../windows/helpcontext.md)|指定可获取有关此元素的用户查看信息在帮助文件的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置帮助文件的名称类型库。|  
|[helpstringcontext](../windows/helpstringcontext.md)|在 .hlp 或 .chm 文件指定帮助主题的 ID。|  
|[helpstringdll](../windows/helpstringdll.md)|指定 DLL 的名称使用执行文档字符串外观 \(本地化\)。|  
|[helpstring](../windows/helpstring.md)|指定一个字符串，该字符串用来描述它所应用的元素。|  
|[hidden](../windows/hidden.md)|指示该项目在面向用户的浏览器存在，但不应显示。|  
|[idl\_module](../windows/idl-module.md)|在指定 DLL 入口点。|  
|[idl\_quote](../windows/idl-quote.md)|可以使用在 Visual C\+\+ 的当前版本不支持的属性或 IDL 构造。|  
|[id](../windows/id.md)|用于成员函数 \(一个属性或将方法指定 DISPID，在接口或调度接口\)。|  
|[iid\_is](../windows/iid-is.md)|指定 COM 接口的 IID 指向接口指针。|  
|[immediatebind](../windows/immediatebind.md)|指示该数据库将立即得到通知到数据对象属性的任何更改。|  
|[importlib](../windows/importlib.md)|使已编译到另一个类型库可用于该类型创建库的类型。|  
|[import](../windows/import.md)|指定包含要从主 .idl 文件中引用的定义的另一个 .idl、 .odl 或头文件。|  
|[包含](../windows/include-cpp.md)|指定在生成的 .idl 文件将包含的一个或多个头文件。|  
|[includelib](../windows/includelib-cpp.md)|导致在生成的 .idl 文件将包含的 .idl 或 .h 文件。|  
|[in](../windows/in-cpp.md)|指示参数是从被调用过程传递给被调用过程。|  
|[last\_is](../windows/last-is.md)|指定要传输的最后一个数组元素的索引。|  
|[LCID](../windows/lcid.md)|可以将区域设置标识符给函数。|  
|[length\_is](../windows/length-is.md)|指定数组元素数会传输的。|  
|[允许](../windows/licensed.md)|指示其适用的 coclass 授权，使用 **IClassFactory2**，并且必须实例化。|  
|[local](../windows/local-cpp.md)|在接口标头可使用 MIDL 编译器作为页眉生成器，当使用。  当在单个函数，即存根未生成一个本地程序。|  
|[max\_is](../windows/max-is.md)|指定有效的数组索引的最大值。|  
|[Module — 模块](../windows/module-cpp.md)|在 .idl 文件中定义了库块。|  
|[ms\_union](../windows/ms-union.md)|控件 nonencapsulated 联合的网络数据表示形式对齐。|  
|[no\_injected\_text](../windows/no-injected-text.md)|由于属性使用，以防止编译器插入代码。|  
|[nonbrowsable](../windows/nonbrowsable.md)|指示接口成员在属性浏览器不应显示。|  
|[不可创建](../windows/noncreatable.md)|定义不能单独实例化的对象。|  
|[nonextensible](../windows/nonextensible.md)|指定 `IDispatch` 实现接口中声明包括只有列表的属性和方法，而不能扩展与运行时的其他成员。|  
|[对象](../windows/object-cpp.md)|标识自定义接口;同义词与自定义属性。|  
|[odl](../windows/odl.md)|标识一个接口作为对象描述语言 \(ODL\)接口。|  
|[custom](../windows/oleautomation.md)|指示接口与自动化兼容。|  
|[选项](../windows/optional-cpp.md)|用于成员函数指定一个可选参数。|  
|[out](../windows/out-cpp.md)|标识从调用过程返回到调用程序的指针参数 \(从服务器向客户端\)。|  
|[pointer\_default](../windows/pointer-default.md)|为除出现在参数列表的顶部指针的所有指针指定默认指针属性。|  
|[说明](../windows/pragma.md)|发出该指定字符串，因此，不带引号字符，到生成的 .idl 文件。|  
|[progid](../windows/progid.md)|为 COM 对象指定 ProgID。|  
|[propget](../windows/propget.md)|指定属性访问器 \(GET\) 函数。|  
|[propputref](../windows/propputref.md)|指定将使用引用而不是值的函数的属性。|  
|[propput](../windows/propput.md)|指定设置功能的属性。|  
|[PTR](../windows/ptr.md)|指定指针作为完整的指针。|  
|[public](../windows/public-cpp-attributes.md)|确保 typedef 将进入类型库，即使未引用从 .idl 文件内。|  
|[范围](../windows/range-cpp.md)|为值设置在运行时的参数或字段指定允许值的大小。|  
|[readonly](../windows/readonly-cpp.md)|禁止分配给变量。|  
|[ref](../windows/ref-cpp.md)|标识引用指针。|  
|[requestedit](../windows/requestedit.md)|指示属性支持 **OnRequestEdit** 通知。|  
|[restricted](../windows/restricted.md)|指定模块、接口或调度接口的库或成员不能随机调用。|  
|[retval](../windows/retval.md)|指定接收该成员的返回值的参数。|  
|[size\_is](../windows/size-is.md)|为大小的指针、大小的指向大小的指针和单项或多维数组指定内存大小分配。|  
|[source](../windows/source-cpp.md)|指示类、属性或方法的成员是事件源。|  
|[string](../windows/string-cpp.md)|指示一维 `char`、 `wchar_t`、 **字节**或等效数组或指针到此数组必须将字符串。|  
|[switch\_is](../windows/switch-is.md)|指定作为选择联合成员的联合的表达式或标识符具有识别力。|  
|[switch\_type](../windows/switch-type.md)|标识为该联合使用的变量的类型具有识别力。|  
|[transmit\_as](../windows/transmit-as.md)|指示编译器将一个存在的类型，客户端和服务器应用程序操作，与一个传输的类型。|  
|[uidefault](../windows/uidefault.md)|指示该类型信息成员是显示的默认成员。用户界面。|  
|[单个](../windows/unique-cpp.md)|指定一个指针。|  
|[usesgetlasterror](../windows/usesgetlasterror.md)|通知调用方，则出现错误，则调用该函数，调用方可以调用 `GetLastError` 检索错误代码时。|  
|[uuid](../windows/uuid-cpp-attributes.md)|为类或接口指定唯一 ID。|  
|[v1\_enum](../windows/v1-enum.md)|命令，指定的枚举类型传输作为 32 位实体，而不是该 16 位默认值。|  
|[vararg](../windows/vararg.md)|指定函数采用参数数目可变。|  
|[vi\_progid](../windows/vi-progid.md)|指定 ProgID 的一个版本中立性窗体。|  
|[wire\_marshal](../windows/wire-marshal.md)|指定在传输将使用而不是一个特定的数据类型的数据类型。|  
  
## 请参阅  
 [Attributes by Group](../windows/attributes-by-group.md)   
 [Attribute Limitations](http://msdn.microsoft.com/zh-cn/6e6c4329-f667-4869-b991-cbe9cb7a8f61)