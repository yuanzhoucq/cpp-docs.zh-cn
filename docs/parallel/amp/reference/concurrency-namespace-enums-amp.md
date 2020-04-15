---
title: 并发命名空间枚举 (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: 2467db27ad36dfcda31dfb5bb45067ada5470d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376318"
---
# <a name="concurrency-namespace-enums-amp"></a>并发命名空间枚举 (AMP)

|||
|-|-|
|[access_type 枚举](#access_type)|[queuing_mode 枚举](#queuing_mode)|

## <a name="access_type-enumeration"></a><a name="access_type"></a>access_type枚举

用于表示对数据的各种类型的访问的枚举类型。

```cpp
enum access_type;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`access_type_auto`|自动选择最适合`access_type`加速器的加速器。|
|`access_type_none`|专用。 分配只能在加速器上访问，而不能在 CPU 上访问。|
|`access_type_read`|共享。 分配在加速器上是可访问的，并且在 CPU 上是可读的。|
|`access_type_read_write`|共享。 分配可在加速器上访问，可在 CPU 上写入。|
|`access_type_write`|共享。 分配在加速器上是可访问的，在 CPU 上既可读又可写。|

## <a name="queuing_mode-enumeration"></a><a name="queuing_mode"></a>queuing_mode枚举

指定加速器上支持的排队模式。

```cpp
enum queuing_mode;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`queuing_mode_immediate`|一种排队模式，用于指定任何命令（例如[，parallel_for_each函数 （C++ AMP））](concurrency-namespace-functions-amp.md#parallel_for_each)在返回调用方后立即发送到相应的加速器设备。|
|`queuing_mode_automatic`|一种排队模式，用于指定在对应于[accelerator_view](accelerator-view-class.md)对象的命令队列上排队的命令。 当调用[accelerator_view：刷新](accelerator-view-class.md#flush)时，命令将发送到设备。|

## <a name="see-also"></a>另请参阅

[Concurrency 命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
