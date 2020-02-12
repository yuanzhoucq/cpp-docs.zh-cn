---
title: 并发命名空间枚举 (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: a4feb2f98fc288fa79c0f9d81e4ed882027eddf8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126941"
---
# <a name="concurrency-namespace-enums-amp"></a>并发命名空间枚举 (AMP)

|||
|-|-|
|[access_type 枚举](#access_type)|[queuing_mode 枚举](#queuing_mode)|

## <a name="access_type"></a>access_type 枚举

用于表示各种类型的数据访问权限的枚举类型。

```cpp
enum access_type;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`access_type_auto`|自动为加速器选择最佳 `access_type`。|
|`access_type_none`|专. 只能在加速器上访问分配，而不能在 CPU 上访问。|
|`access_type_read`|共享. 分配可在加速器上访问，并且在 CPU 上可读。|
|`access_type_read_write`|共享. 分配可在加速器上访问，并且在 CPU 上可写。|
|`access_type_write`|共享. 分配可在加速器上访问，并且在 CPU 上可读写。|

## <a name="queuing_mode"></a>queuing_mode 枚举

指定加速器支持的排队模式。

```cpp
enum queuing_mode;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`queuing_mode_immediate`|一种队列模式，指定任何命令（例如[Parallel_for_each 函数（C++ AMP））](concurrency-namespace-functions-amp.md#parallel_for_each)在返回到调用方后立即发送到相应的加速器设备。|
|`queuing_mode_automatic`|队列模式，指定在与[accelerator_view](accelerator-view-class.md)对象对应的命令队列中对命令进行排队。 调用[accelerator_view：： flush](accelerator-view-class.md#flush)时，会将命令发送到设备。|

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
