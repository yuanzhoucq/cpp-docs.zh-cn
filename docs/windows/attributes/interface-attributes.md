---
title: 接口属性（C++ COM）
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
ms.openlocfilehash: 81a88ddfd74f20fa57ef615c988ba9786f41c1ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214820"
---
# <a name="interface-attributes"></a>接口特性

以下属性适用于[接口（或 __interface）](../../cpp/interface.md) C++关键字。

|特性|描述|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|指定指示 MIDL 编译器定义 COM 接口的同步和异步版本的 UUID。|
|[custom](custom-cpp.md)|允许您定义自己的属性。|
|[dispinterface](dispinterface.md)|将一个接口作为调度接口置于 .idl 文件中。|
|[dual](dual.md)|将一个接口作为双重接口放置在 .idl 文件中。|
|[export](export.md)|导致将数据结构放置在 .idl 文件中。|
|[helpcontext](helpcontext.md)|指定一个上下文 ID，该 ID 允许用户在帮助文件中查看有关此元素的信息。|
|[helpfile](helpfile.md)|设置类型库的帮助文件的名称。|
|[helpstring](helpstring.md)|指定一个字符串，用于描述应用该字符串的元素。|
|[helpstringcontext](helpstringcontext.md)|指定 .hlp 或 .chm 文件中帮助主题的 ID。|
|[helpstringdll](helpstringdll.md)|指定要用于执行文档字符串查找（本地化）的 DLL 的名称。|
|[hidden](hidden.md)|指示该项存在，但不应在面向用户的浏览器中显示。|
|[library_block](library-block.md)|将构造置于 .idl 文件的库块内。|
|[local](local-cpp.md)|允许在接口标头中使用 MIDL 编译器时将其用作标头生成器。 在单独的函数中使用时，指定不会为其生成存根的本地过程。|
|[nonextensible](nonextensible.md)|指定 `IDispatch` 实现仅包含接口说明中列出的属性和方法，而不能在运行时与其他成员一起扩展。 此属性仅在[双重](dual.md)接口上有效。|
|[odl](odl.md)|将接口标识为对象描述语言（ODL）接口。|
|[object](object-cpp.md)|标识自定义接口。|
|[oleautomation](oleautomation.md)|指示接口与自动化兼容。|
|[pointer_default](pointer-default.md)|为除 "参数列表" 中显示的顶级指针之外的所有指针指定默认指针特性。|
|[ptr](ptr.md)|将指针指定为完全指针。|
|[restricted](restricted.md)|指定不能任意调用库的哪些成员。|
|[uuid](uuid-cpp-attributes.md)|提供库的唯一 ID|

您必须遵守以下定义接口规则：

- [__Stdcall](../../cpp/stdcall.md)默认调用约定。

- 如果你没有提供 GUID，则为你提供 GUID。

- 不允许使用重载方法。

当未指定[uuid](uuid-cpp-attributes.md)属性并在不同的属性项目中使用相同的接口名称时，将生成相同的 GUID。

## <a name="see-also"></a>请参阅

[按用法分的特性](attributes-by-usage.md)
