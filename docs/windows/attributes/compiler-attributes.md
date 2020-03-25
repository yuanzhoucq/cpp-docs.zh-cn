---
title: 编译器属性（C++ COM）
ms.date: 10/02/2018
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
ms.openlocfilehash: f8eb15645049085acc047e41d0a4ea769d359871
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168274"
---
# <a name="compiler-attributes"></a>编译器特性

编译器属性提供多种功能。

|Attribute|说明|
|---------------|-----------------|
|[emitidl](emitidl.md)|确定是否将处理所有后续 IDL 特性并将其放置在生成的 .idl 文件中。|
|[event_receiver](event-receiver.md)|创建事件接收器。|
|[event_source](event-source.md)|创建事件源。|
|[export](export.md)|导致将数据结构放置在 .idl 文件中。|
|[implements](implements-cpp.md)|指定强制成为 IDL 组件类成员的调度接口。|
|[importidl](importidl.md)|将指定的 .idl 文件插入生成的 .idl 文件。|
|[importlib](importlib.md)|使已编译到另一个类型库中的类型可供所创建的类型库使用。|
|[includelib](includelib-cpp.md)|导致在生成的 .idl 文件中包含 .idl 或 .h 文件。|
|[library_block](library-block.md)|将构造置于 .idl 文件的库块内。|
|[no_injected_text](no-injected-text.md)|阻止编译器将代码注入到属性使用的结果中。|
|[satype](satype.md)|指定 `SAFEARRAY`的数据类型。|
|[version](version-cpp.md)|标识接口或类的多个版本中的特定版本。|

## <a name="see-also"></a>另请参阅

[按组分的特性](attributes-by-group.md)
