---
title: 独立属性（C++ COM）
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: a7df91bbb1c6929b08d8cd867be9f13ce0c35b91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166160"
---
# <a name="stand-alone-attributes"></a>独立特性

独立属性对C++关键字不起作用，但更类似于代码行。 独立的 attribute 语句需要在行的末尾使用分号。

## <a name="stand-alone-attribute-list"></a>独立属性列表

|Attribute|说明|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|向生成的标头文件发出指定的字符串（不含引号字符）。|
|[custom](custom-cpp.md)|允许您定义自己的属性。|
|[db_command](db-command.md)|创建 OLE DB 命令。|
|[emitidl](emitidl.md)|确定是否将处理所有后续 IDL 特性并将其放置在生成的 .idl 文件中。|
|[idl_module](idl-module.md)|指定 DLL 中的入口点。|
|[idl_quote](idl-quote.md)|允许你使用当前版本的视觉对象C++不支持的 IDL 构造，并将其传递到生成的 .idl 文件。|
|[import](import.md)|指定另一个 .idl、odl 或 .h 文件，其中包含要从您的主 .idl 文件引用的定义。|
|[importidl](importidl.md)|将指定的 .idl 文件插入生成的 .idl 文件|
|[importlib](importlib.md)|使已编译到另一个类型库中的类型可供所创建的类型库使用。|
|[include](include-cpp.md)|指定要包含在生成的 .idl 文件中的一个或多个标头文件。|
|[includelib](includelib-cpp.md)|导致在生成的 .idl 文件中包含 .idl 或 .h 文件。|
|[library_block](library-block.md)|将构造置于 .idl 文件的库块内。|
|[module](module-cpp.md)|定义.Idl 文件中的库块。|
|[no_injected_text](no-injected-text.md)|阻止编译器将代码注入到属性使用的结果中。|
|[pragma](pragma.md)|向生成的 .idl 文件发出指定的字符串（不含引号字符）。|

## <a name="see-also"></a>另请参阅

[按用法分的特性](attributes-by-usage.md)
