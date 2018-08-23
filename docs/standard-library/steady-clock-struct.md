---
title: steady_clock 结构 | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::steady_clock
dev_langs:
- C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53f4deb0bfe9439011f75cd22d0d52b74dae9c1f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959720"
---
# <a name="steadyclock-struct"></a>steady_clock 结构

表示*稳定*时钟。

## <a name="syntax"></a>语法

```cpp
struct steady_clock;
```

## <a name="remarks"></a>备注

在 Windows 中，`steady_clock`包装`QueryPerformanceCounter`函数。

如果首次调用 `now` 返回的值始终小于或等于后续调用 `now` 返回的值，则为单调时钟。 如果它是单调时钟并且时钟计时周期之间的时间是常量，则为稳定时钟。

`high_resolution_clock` 是的 typedef `steady_clock`。

### <a name="public-typedefs"></a>公共 typedef

|name|描述|
|----------|-----------------|
|`steady_clock::duration`|同义词`nanoseconds`中定义\<chrono >。|
|`steady_clock::period`|同义词`nano`中定义\<比率 >。|
|`steady_clock::rep`|同义词**长****长**，用于表示中包含的实例化的时钟计时周期数的类型`duration`。|
|`steady_clock::time_point`|`chrono::time_point<steady_clock>` 的同义词。|

## <a name="public-functions"></a>公共函数

|函数|描述|
|--------------|-----------------|
|`now`|返回当前时间作为`time_point`值。|

## <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|`steady_clock::is_steady`|持有 **，则返回 true**。 `steady_clock` 是*稳定的*。|

## <a name="requirements"></a>要求

**标头：** \<chrono >

**命名空间：** std::chrono

## <a name="see-also"></a>请参阅

- [头文件引用](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock 结构](../standard-library/system-clock-structure.md)
