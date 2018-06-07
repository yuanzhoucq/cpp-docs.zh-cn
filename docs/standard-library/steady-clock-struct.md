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
ms.openlocfilehash: 5445379597c4fefcd657303a05c33b6509d54d2e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569893"
---
# <a name="steadyclock-struct"></a>steady_clock 结构

表示*稳定*时钟。

## <a name="syntax"></a>语法

```cpp
struct steady_clock;
```

## <a name="remarks"></a>备注

在 Windows 上，`steady_clock`包装`QueryPerformanceCounter`函数。

如果首次调用 `now` 返回的值始终小于或等于后续调用 `now` 返回的值，则为单调时钟。 如果它是单调时钟并且时钟计时周期之间的时间是常量，则为稳定时钟。

`high_resolution_clock` 是的 typedef `steady_clock`。

### <a name="public-typedefs"></a>公共 typedef

|name|描述|
|----------|-----------------|
|`steady_clock::duration`|同义词`nanoseconds`在中定义\<chrono >。|
|`steady_clock::period`|同义词`nano`在中定义\<比率 >。|
|`steady_clock::rep`|同义词**长****长**，用于表示中的包含实例化的时钟计时周期数的类型`duration`。|
|`steady_clock::time_point`|`chrono::time_point<steady_clock>` 的同义词。|

## <a name="public-functions"></a>公共函数

|函数|描述|
|--------------|-----------------|
|`now`|返回在当前时间`time_point`值。|

## <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|`steady_clock::is_steady`|保存 `true`。 `steady_clock` 是*稳定的*。|

## <a name="requirements"></a>要求

**标头：** \<chrono >

**命名空间：** std::chrono

## <a name="see-also"></a>请参阅

- [头文件引用](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock 结构](../standard-library/system-clock-structure.md)
