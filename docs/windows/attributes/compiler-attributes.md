---
title: 编译器特性 (c + + COM) |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 9f0483676fd0dd60d893f8931511083d369539dd
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790348"
---
# <a name="compiler-attributes"></a>编译器特性

编译器特性提供各种功能。

|特性|描述|
|---------------|-----------------|
|[emitidl](emitidl.md)|确定是否将处理并放置在生成的.idl 文件中所有后续的 IDL 特性。|
|[event_receiver](event-receiver.md)|创建事件接收器。|
|[event_source](event-source.md)|创建事件源。|
|[export](export.md)|导致要放置在.idl 文件中的数据结构。|
|[实现](implements-cpp.md)|指定强制 IDL 组件类的成员的调度接口。|
|[importidl](importidl.md)|将指定的.idl 文件插入到生成的.idl 文件。|
|[importlib](importlib.md)|使已编译到另一个类型库中的类型可供所创建的类型库使用。|
|[includelib](includelib-cpp.md)|导致要生成的.idl 文件中包含的.idl 或.h 文件。|
|[library_block](library-block.md)|将放置在.idl 文件的库块中的构造。|
|[no_injected_text](no-injected-text.md)|禁止编译器注入代码作为特性使用结果。|
|[satype](satype.md)|指定的数据类型`SAFEARRAY`。|
|[version](version-cpp.md)|标识的接口或类的多个版本间的特定版本。|

## <a name="see-also"></a>请参阅

[按组分的特性](attributes-by-group.md)