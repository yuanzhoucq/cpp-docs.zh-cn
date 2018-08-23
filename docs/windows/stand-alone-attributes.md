---
title: 独立特性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standalone attributes
- attributes [C++], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6562a1de8baa9a5805f044233b97bf8dd8840638
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613753"
---
# <a name="stand-alone-attributes"></a>独立特性
独立属性不是 c + + 关键字进行操作，但更像是代码行。 独立特性语句需要行尾的分号。
  
|特性|描述|
|---------------|-----------------|
|[cpp_quote](../windows/cpp-quote.md)|将指定的字符串，而无需引号字符，发送到生成的头文件。|
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|
|[db_command](../windows/db-command.md)|创建 OLE DB 命令。|
|[emitidl](../windows/emitidl.md)|确定是否将处理并放置在生成的.idl 文件中所有后续的 IDL 特性。|
|[idl_module](../windows/idl-module.md)|在 DLL 中指定的入口点。|
|[idl_quote](../windows/idl-quote.md)|可以使用不支持当前版本的 Visual c + + 中的 IDL 构造并将它们传递到生成的.idl 文件。|
|[import](../windows/import.md)|指定包含你想要从主.idl 文件中引用的定义的另一个.idl、.odl 或.h 文件。|
|[importidl](../windows/importidl.md)|将指定的.idl 文件插入到生成的.idl 文件|
|[importlib](../windows/importlib.md)|使已编译到另一个类型库中的类型可供所创建的类型库使用。|
|[include](../windows/include-cpp.md)|指定要包括在生成的.idl 文件中的一个或多个标头文件。|
|[includelib](../windows/includelib-cpp.md)|导致要生成的.idl 文件中包含的.idl 或.h 文件。|
|[library_block](../windows/library-block.md)|将放置在.idl 文件的库块中的构造。|
|[模块](../windows/module-cpp.md)|定义.Idl 文件中的库块。|
|[no_injected_text](../windows/no-injected-text.md)|禁止编译器注入代码作为特性使用结果。|
|[pragma](../windows/pragma.md)|将指定的字符串，而无需引号字符，发送到生成的.idl 文件。|
  
## <a name="see-also"></a>请参阅
 [按用法分的特性](../windows/attributes-by-usage.md)