---
title: 按用法分的特性
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: f6567a7866516c09bca03fa9f3d3aa5aa997b6b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148430"
---
# <a name="attributes-by-usage"></a>按用法分的特性

本主题列出根据属性C++应用于的语言元素。

如果属性优先于不在该属性的范围内的元素，特性块视为注释。

|特性|描述|
|---------------|-----------------|
|[模块特性](module-attributes.md)|适用于[模块](module-cpp.md)属性。|
|[接口特性](interface-attributes.md)|适用于[__interface](../../cpp/interface.md) C++关键字。|
|[类特性](class-attributes.md)|适用于C++关键字。|
|[方法特性](method-attributes.md)|适用于类、 组件类或接口中的方法。|
|[参数特性](parameter-attributes.md)|适用于的类或接口中的方法的参数。|
|[数据成员特性](data-member-attributes.md)|适用于类、 组件类或接口中的数据成员。|
|[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)|适用于C++关键字。|
|[数组特性](array-attributes.md)|适用于数组或`SAFEARRAY`s。|
|[独立特性](stand-alone-attributes.md)|运行更像是代码行，但不会无法运行在C++关键字。 独立特性语句需要行尾的分号。|
|[自定义属性](custom-attributes-cpp.md)|允许用户以扩展元数据。|

## <a name="module-attributes"></a>模块特性
以下属性只能应用于[模块](module-cpp.md)属性。

|特性|描述|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|指定要用于执行文档字符串查找 （本地化） DLL 的名称。|

## <a name="interface-attributes"></a>接口特性

以下属性应用于[接口 （或 __interface）](../../cpp/interface.md) C++关键字。

|特性|描述|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|指定指示 MIDL 编译器定义的 COM 接口的同步和异步版本的 UUID。|
|[custom](custom-cpp.md)|可以定义自己的属性。|
|[dispinterface](dispinterface.md)|将一个接口作为调度接口置于 .idl 文件中。|
|[dual](dual.md)|双重接口.idl 文件中放置一个接口。|
|[export](export.md)|导致要放置在.idl 文件中的数据结构。|
|[helpcontext](helpcontext.md)|指定允许用户查看有关此帮助文件中的元素的信息的上下文 ID。|
|[helpfile](helpfile.md)|设置类型库的帮助文件的名称。|
|[helpstring](helpstring.md)|指定一个字符串，用于描述应用该字符串的元素。|
|[helpstringcontext](helpstringcontext.md)|在.hlp 或.chm 文件中指定的帮助主题的 ID。|
|[helpstringdll](helpstringdll.md)|指定要用于执行文档字符串查找 （本地化） DLL 的名称。|
|[hidden](hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|
|[library_block](library-block.md)|将放置在.idl 文件的库块中的构造。|
|[local](local-cpp.md)|可以使用 MIDL 编译器为标头生成器界面标头中使用时。 单个函数中使用时，将指定为其生成无存根 （stub） 的本地过程。|
|[nonextensible](nonextensible.md)|指定`IDispatch`实现仅包括属性和方法的接口描述中列出，并在运行时不能与其他成员扩展。 此属性才有效上[双](dual.md)接口。|
|[odl](odl.md)|标识为对象描述语言 (ODL) 接口的接口。|
|[object](object-cpp.md)|标识的自定义的接口。|
|[oleautomation](oleautomation.md)|指示接口使用自动化兼容。|
|[pointer_default](pointer-default.md)|在参数列表中指定除顶级指针显示的所有指针的默认指针特性。|
|[ptr](ptr.md)|将一个指针，指定为完整的指针。|
|[restricted](restricted.md)|指定库中的哪些成员不能任意调用。|
|[uuid](uuid-cpp-attributes.md)|提供的库的唯一 ID|

您必须遵守这些规则用于定义一个接口：

- 默认调用约定是[__stdcall](../../cpp/stdcall.md)。

- 如果未提供一个将为您提供一个 GUID。

- 不允许使用任何重载的方法。

未指定时[uuid](uuid-cpp-attributes.md)属性，并在不同的属性项目中使用相同的接口名称，就会生成相同的 GUID。

## <a name="see-also"></a>请参阅

[COM 和 .NET 的 C++ 属性](cpp-attributes-com-net.md)<br/>
[按组分的特性](attributes-by-group.md)<br/>
[按字母顺序的特性参考](attributes-alphabetical-reference.md)