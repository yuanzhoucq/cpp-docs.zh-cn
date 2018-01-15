---
title: "接口特性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- attributes [C++], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ff84939b3211633e199066e1a38da2e91efb1c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="interface-attributes"></a>接口特性
下列属性适用于[接口 （或 __interface）](../cpp/interface.md) c + + 关键字。  
  
|特性|描述|  
|---------------|-----------------|  
|[async_uuid](../windows/async-uuid.md)|指定指示 MIDL 编译器定义的 COM 接口的同步和异步版本的 UUID。|  
|[自定义](../windows/custom-cpp.md)|你可以定义你自己的特性。|  
|[dispinterface](../windows/dispinterface.md)|将一个接口作为调度接口置于 .idl 文件中。|  
|[dual](../windows/dual.md)|将接口置于.idl 文件中作为双重接口。|  
|[export](../windows/export.md)|会导致数据结构，用于放置在.idl 文件。|  
|[helpcontext](../windows/helpcontext.md)|指定允许用户查看有关此帮助文件中的元素信息的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置类型库的帮助文件的名称。|  
|[helpstring](../windows/helpstring.md)|指定用于描述应用于元素的字符字符串。|  
|[helpstringcontext](../windows/helpstringcontext.md)|.Hlp 或.chm 文件中指定的帮助主题的 ID。|  
|[helpstringdll](../windows/helpstringdll.md)|指定要用于执行文档字符串查找 （本地化） 的 dll 的名称。|  
|[hidden](../windows/hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|  
|[library_block](../windows/library-block.md)|将.idl 文件的库块中的构造。|  
|[本地](../windows/local-cpp.md)|可用作接口标头中使用时的标头生成器 MIDL 编译器。 当使用单个函数中，指定为其生成没有存根 （stub） 的本地过程。|  
|[nonextensible](../windows/nonextensible.md)|指定`IDispatch`实现仅包括的属性和方法的接口描述中列出，并在运行时不能与其他成员扩展。 此属性才有效上[双重](../windows/dual.md)接口。|  
|[odl](../windows/odl.md)|标识为对象描述语言 (ODL) 接口的接口。|  
|[对象](../windows/object-cpp.md)|标识的自定义的接口。|  
|[oleautomation](../windows/oleautomation.md)|指示接口是与自动化兼容。|  
|[pointer_default](../windows/pointer-default.md)|参数列表中指定除顶级指针显示的所有指针的指针默认属性。|  
|[ptr](../windows/ptr.md)|将一个指针指定为完整的指针。|  
|[restricted](../windows/restricted.md)|指定库中的哪些成员不能任意调用。|  
|[uuid](../windows/uuid-cpp-attributes.md)|提供的库的唯一 ID|  
  
 你必须遵循这些规则的定义的接口：  
  
-   默认调用约定是[__stdcall](../cpp/stdcall.md)。  
  
-   如果未提供一个，将为你提供一个 GUID。  
  
-   允许使用没有重载的方法。  
  
 未指定时[uuid](../windows/uuid-cpp-attributes.md)属性，并在不同的属性项目中使用相同的接口名称，将生成相同的 GUID。  
  
## <a name="see-also"></a>请参阅  
 [按用法分的特性](../windows/attributes-by-usage.md)