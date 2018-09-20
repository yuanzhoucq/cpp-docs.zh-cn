---
title: 并发命名空间枚举 (AMP) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs:
- C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4f842b799a81179fa1a612e652aae391ca3375d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435657"
---
# <a name="concurrency-namespace-enums-amp"></a>并发命名空间枚举 (AMP)

|||
|-|-|
|[access_type 枚举](#access_type)|[queuing_mode 枚举](#queuing_mode)|

##  <a name="access_type"></a>  access_type 枚举

用于表示对数据的访问的各种类型的枚举类型。

```
enum access_type;
```
### <a name="values"></a>值

|名称|描述|
|----------|-----------------|
|`access_type_auto`|自动选择最佳`access_type`加速器。|
|`access_type_none`|专用。 分配才可访问加速器上而不是 CPU。|
|`access_type_read`|共享。 分配可通过快捷键访问，并且是在 CPU 上可读。|
|`access_type_read_write`|共享。 分配可通过快捷键访问，并且是在 CPU 上可写。|
|`access_type_write`|共享。 分配可通过快捷键访问，并且是可读且在 CPU 上可写。|

##  <a name="queuing_mode"></a>  queuing_mode 枚举

指定在快捷键支持的排队模式。

```
enum queuing_mode;
```
### <a name="values"></a>值

|名称|描述|
|----------|-----------------|
|`queuing_mode_immediate`|指定任何的排队模式命令，例如， [parallel_for_each 函数 (c + + AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)，只要它们返回给调用方发送到相应的加速器设备。|
|`queuing_mode_automatic`|指定命令必须排对应的命令队列的排队模式[accelerator_view](accelerator-view-class.md)对象。 命令发送到设备时[accelerator_view:: flush](accelerator-view-class.md#flush)调用。|

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
