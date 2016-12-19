---
title: "Stand-Alone Attributes | Microsoft Docs"
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
  - "standalone attributes"
  - "attributes [C++], standalone"
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Stand-Alone Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

独立属性不对 c. C\+\+ 关键字，而是更象代码行。  独立属性语句需要一个分号在行尾。  
  
|特性|说明|  
|--------|--------|  
|[cpp\_quote](../windows/cpp-quote.md)|发出该指定字符串，因此，不带引号字符，以生成的头文件。|  
|[custom](../windows/custom-cpp.md)|使您可以定义拥有该属性。|  
|[db\_command](../windows/db-command.md)|创建一个 OLE DB 命令。|  
|[emitidl](../windows/emitidl.md)|确定所有后续 IDL 特性是否在生成的 .idl 文件进行处理和放置。|  
|[idl\_module](../windows/idl-module.md)|在指定 DLL 入口点。|  
|[idl\_quote](../windows/idl-quote.md)|可以使用在 Visual C\+\+ 的当前版本不支持的 IDL 构造并将它们传递到生成的 .idl 文件。|  
|[import](../windows/import.md)|指定包含要从主 .idl 文件中引用的定义的其他 .idl、 .odl 或 .h 文件。|  
|[importidl](../windows/importidl.md)|插入指定的 .idl 文件添加到生成的 .idl 文件中|  
|[importlib](../windows/importlib.md)|使已编译到另一个类型库可用于该类型创建库的类型。|  
|[包含](../windows/include-cpp.md)|指定在生成的 .idl 文件将包含的一个或多个头文件。|  
|[includelib](../windows/includelib-cpp.md)|导致在生成的 .idl 文件将包含的 .idl 或 .h 文件。|  
|[library\_block](../windows/library-block.md)|放在 .idl 文件的库中的构造块。|  
|[Module — 模块](../windows/module-cpp.md)|在 .idl 文件中定义了库块。|  
|[no\_injected\_text](../windows/no-injected-text.md)|由于属性使用，以防止编译器插入代码。|  
|[说明](../windows/pragma.md)|发出该指定字符串，因此，不带引号字符，到生成的 .idl 文件。|  
  
## 请参阅  
 [Attributes by Usage](../windows/attributes-by-usage.md)