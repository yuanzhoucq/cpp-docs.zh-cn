---
title: "Interface Attributes | Microsoft Docs"
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
  - "interface attributes"
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Interface Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下特性应用于 [接口 \(或 \_\_interface\)](../cpp/interface.md) C\+\+ 关键字。  
  
|特性|说明|  
|--------|--------|  
|[async\_uuid](../windows/async-uuid.md)|指定处理 MIDL 编译器定义 COM 接口的同步和异步版本的 UUID。|  
|[custom](../windows/custom-cpp.md)|使您可以定义拥有该属性。|  
|[dispinterface](../windows/dispinterface.md)|在 .idl 文件中放置一个接口作为调度接口。|  
|[dual](../windows/dual.md)|在 .idl 文件中放置一个接口该接口。|  
|[export](../windows/export.md)|在 .idl 文件中创建一个数据结构将。|  
|[helpcontext](../windows/helpcontext.md)|指定可获取有关此元素的用户查看信息在帮助文件的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置帮助文件的名称类型库。|  
|[helpstring](../windows/helpstring.md)|指定一个字符串，该字符串用来描述它所应用的元素。|  
|[helpstringcontext](../windows/helpstringcontext.md)|在 .hlp 或 .chm 文件指定帮助主题的 ID。|  
|[helpstringdll](../windows/helpstringdll.md)|指定 DLL 的名称使用执行文档字符串外观 \(本地化\)。|  
|[hidden](../windows/hidden.md)|指示该项目在面向用户的浏览器存在，但不应显示。|  
|[library\_block](../windows/library-block.md)|放在 .idl 文件的库中的构造块。|  
|[local](../windows/local-cpp.md)|在接口标头可使用 MIDL 编译器作为页眉生成器，当使用。  当在单个函数，即存根未生成一个本地程序。|  
|[nonextensible](../windows/nonextensible.md)|指定 `IDispatch` 实现接口中声明包括只有列表的属性和方法，而不能扩展与运行时的其他成员。  此属性仅适用于 [双](../windows/dual.md) 接口。|  
|[odl](../windows/odl.md)|标识一个接口作为对象描述语言 \(ODL\)接口。|  
|[对象](../windows/object-cpp.md)|标识自定义接口。|  
|[custom](../windows/oleautomation.md)|指示接口与自动化兼容。|  
|[pointer\_default](../windows/pointer-default.md)|为除出现在参数列表的顶部指针的所有指针指定默认指针属性。|  
|[PTR](../windows/ptr.md)|指定指针作为完整的指针。|  
|[restricted](../windows/restricted.md)|指定库的哪些成员不能随机调用。|  
|[uuid](../windows/uuid-cpp-attributes.md)|用于库提供唯一 ID|  
  
 必须对定义接口遵循下列规则:  
  
-   调用约定的默认值为 [\_\_stdcall](../cpp/stdcall.md)。  
  
-   ，如果不提供一个 GUID，而不是提供。  
  
-   重载方法不允许的。  
  
 当未指定 [uuid](../windows/uuid-cpp-attributes.md) 属性和不使用同一个接口名称在其他属性项目时，具有相同的 GUID 生成。  
  
## 请参阅  
 [Attributes by Usage](../windows/attributes-by-usage.md)