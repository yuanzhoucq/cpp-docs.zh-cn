---
title: 独立特性 (c + + COM) |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0df8cb1def78e3a7b564f268eb1b3b0a2069fb11
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062842"
---
# <a name="stand-alone-attributes"></a>独立特性

独立属性不是 c + + 关键字进行操作，但更像是代码行。 独立特性语句需要行尾的分号。

## <a name="stand-alone-attribute-list"></a>独立的属性列表

|特性|描述|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|将指定的字符串，而无需引号字符，发送到生成的头文件。|
|[custom](custom-cpp.md)|你可以定义自己的属性。|
|[db_command](db-command.md)|创建 OLE DB 命令。|
|[emitidl](emitidl.md)|确定是否将处理并放置在生成的.idl 文件中所有后续的 IDL 特性。|
|[idl_module](idl-module.md)|在 DLL 中指定的入口点。|
|[idl_quote](idl-quote.md)|可以使用不支持当前版本的 Visual c + + 中的 IDL 构造并将它们传递到生成的.idl 文件。|
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