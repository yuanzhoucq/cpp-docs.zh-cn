---
title: 编译器特性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c1ce698992f1f34434a476be83da6f4697f619c
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316531"
---
# <a name="compiler-attributes"></a>编译器特性

编译器特性提供各种功能。

|特性|描述|
|---------------|-----------------|
|[emitidl](../windows/emitidl.md)|确定是否将处理并放置在生成的.idl 文件中所有后续的 IDL 特性。|
|[event_receiver](../windows/event-receiver.md)|创建事件接收器。|
|[event_source](../windows/event-source.md)|创建事件源。|
|[export](../windows/export.md)|导致要放置在.idl 文件中的数据结构。|
|[实现](../windows/implements-cpp.md)|指定强制 IDL 组件类的成员的调度接口。|
|[importidl](../windows/importidl.md)|将指定的.idl 文件插入到生成的.idl 文件。|
|[importlib](../windows/importlib.md)|使已编译到另一个类型库中的类型可供所创建的类型库使用。|
|[includelib](../windows/includelib-cpp.md)|导致要生成的.idl 文件中包含的.idl 或.h 文件。|
|[library_block](../windows/library-block.md)|将放置在.idl 文件的库块中的构造。|
|[no_injected_text](../windows/no-injected-text.md)|禁止编译器注入代码作为特性使用结果。|
|[satype](../windows/satype.md)|指定的数据类型`SAFEARRAY`。|
|[version](../windows/version-cpp.md)|标识的接口或类的多个版本间的特定版本。|

## <a name="see-also"></a>请参阅

[按组分的特性](../windows/attributes-by-group.md)