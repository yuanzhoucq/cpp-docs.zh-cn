---
title: 独立特性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: 7dd1f35add3b23dbd81e32a1600481eec79fe7d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407258"
---
# <a name="stand-alone-attributes"></a>独立特性

独立属性不会进行操作C++关键字，但较更像是代码行。 独立特性语句需要行尾的分号。

## <a name="stand-alone-attribute-list"></a>独立的属性列表

|特性|描述|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|将指定的字符串，而无需引号字符，发送到生成的头文件。|
|[custom](custom-cpp.md)|你可以定义自己的属性。|
|[db_command](db-command.md)|创建 OLE DB 命令。|
|[emitidl](emitidl.md)|确定是否将处理并放置在生成的.idl 文件中所有后续的 IDL 特性。|
|[idl_module](idl-module.md)|在 DLL 中指定的入口点。|
|[idl_quote](idl-quote.md)|可使用视觉对象的当前版本中不支持的 IDL 构造C++并将它们传递到生成的.idl 文件。|
|[import](import.md)|指定包含你想要从主.idl 文件中引用的定义的另一个.idl、.odl 或.h 文件。|
|[importidl](importidl.md)|将指定的.idl 文件插入到生成的.idl 文件|
|[importlib](importlib.md)|使已编译到另一个类型库中的类型可供所创建的类型库使用。|
|[include](include-cpp.md)|指定要包括在生成的.idl 文件中的一个或多个标头文件。|
|[includelib](includelib-cpp.md)|导致要生成的.idl 文件中包含的.idl 或.h 文件。|
|[library_block](library-block.md)|将放置在.idl 文件的库块中的构造。|
|[module](module-cpp.md)|定义.Idl 文件中的库块。|
|[no_injected_text](no-injected-text.md)|禁止编译器注入代码作为特性使用结果。|
|[pragma](pragma.md)|将指定的字符串，而无需引号字符，发送到生成的.idl 文件。|

## <a name="see-also"></a>请参阅

[按用法分的特性](attributes-by-usage.md)