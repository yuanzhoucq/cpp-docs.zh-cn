---
title: high_resolution_clock 结构 |Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.technology: cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::high_resolution_clock
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b00b20e7cea4fa24b37ad33d5536eb9844e6953
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269119"
---
# <a name="steadyclock-struct"></a>steady_clock 结构

表示*high_resolution*时钟。

## <a name="syntax"></a>语法

```cpp
class high_resolution_clock
```

## <a name="members"></a>成员

### <a name="typedefs"></a>Typedef

|name|描述|
|----------|-----------------|
|`duration`|同义词`nanoseconds`中定义\<chrono >。|
|`period`|同义词`nano`中定义\<比率 >。|
|`rep`|同义词**长** **长**，用于表示中包含的实例化的时钟计时周期数的类型`duration`。|
|`time_point`|`chrono::time_point<high_resolution_clock>` 的同义词。|

## <a name="functions"></a>函数

|||
|-|-|
|`now`|返回当前时间作为`time_point`值。|

## <a name="constants"></a>常量

|名称|描述|
|----------|-----------------|
|`is_steady`|持有 **，则返回 true**。 `high_resolution_clock` 是*稳定的*。|
