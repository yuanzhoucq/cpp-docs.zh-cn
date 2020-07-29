---
title: system_clock 结构
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
ms.openlocfilehash: 4e530887e7c8cf26e8969a839702286913da9b67
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224573"
---
# <a name="system_clock-structure"></a>system_clock 结构

表示基于系统实时时钟的*时钟类型*。

## <a name="syntax"></a>语法

```cpp
struct system_clock;
```

## <a name="remarks"></a>备注

*时钟类型*用于获取作为 UTC 的当前时间。 该类型包含[持续时间](../standard-library/duration-class.md)的实例化和类模板 [time_point](../standard-library/time-point-class.md)，并定义返回时间的静态成员函数 `now()`。

如果首次调用 `now()` 返回的值始终小于或等于后续调用 `now()` 返回的值，则为单调** 时钟。

如果它是单调** 时钟并且时钟计时周期之间的时间是常量，则为稳定** 时钟。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`system_clock::duration`|`duration<rep, period>` 的同义词。|
|`system_clock::period`|该类型的同义词，用于表示在包含的 `duration` 的实例化中的时钟周期。|
|`system_clock::rep`|该类型的同义词，用于表示在包含的 `duration` 的实例化中的时钟计时周期数。|
|`system_clock::time_point`|`time_point<Clock, duration>` 的同义词，其中 `Clock` 是时钟类型本身的同义词，或是另一种基于同一时期并具有相同嵌套 `duration` 类型的时钟类型的同义词。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[from_time_t](#from_time_t)|静态。 返回最接近指定的时间的 `time_point`。|
|[现在](#now)|静态。 返回当前日期。|
|[to_time_t](#to_time_t)|静态。 返回最接近指定 `time_point` 的 `time_t` 对象。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[system_clock::is_monotonic 常量](#is_monotonic_constant)|指定时钟类型是否为单调。|
|[system_clock::is_steady 常量](#is_steady_constant)|指定时钟类型是否为稳定。|

## <a name="requirements"></a>要求

**标头：**\<chrono>

**命名空间：** std::chrono

## <a name="system_clockfrom_time_t"></a><a name="from_time_t"></a>system_clock：： from_time_t

返回[time_point](../standard-library/time-point-class.md)的静态方法，该方法最接近*Tm*表示的时间。

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>参数

*费*\
一个 [time_t](../c-runtime-library/standard-types.md) 对象。

## <a name="system_clockis_monotonic-constant"></a><a name="is_monotonic_constant"></a>system_clock：： is_monotonic 常量

指定时钟类型是否为单调的静态值。

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>返回值

在此实现中， `system_clock::is_monotonic` 始终返回 **`false`** 。

### <a name="remarks"></a>备注

如果首次调用 `now()` 返回的值始终小于或等于后续调用 `now()` 返回的值，则为单调** 时钟。

## <a name="system_clockis_steady-constant"></a><a name="is_steady_constant"></a>system_clock：： is_steady 常量

指定时钟类型是否为*稳定*的静态值。

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>返回值

在此实现中， `system_clock::is_steady` 始终返回 **`false`** 。

### <a name="remarks"></a>备注

如果它是单调[](#is_monotonic_constant)时钟并且时钟计时周期之间的时间是常量，则为稳定** 时钟。

## <a name="system_clocknow"></a><a name="now"></a>system_clock：：现在

返回当前时间的静态方法。

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>返回值

表示当前对象的 [time_point](../standard-library/time-point-class.md) 对象。

## <a name="system_clockto_time_t"></a><a name="to_time_t"></a>system_clock：： to_time_t

返回[time_t](../c-runtime-library/standard-types.md)的静态方法，该方法最接近于*时间*表示的时间。

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>参数

*阶段*\
一个 [time_point](../standard-library/time-point-class.md) 对象。

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[steady_clock 结构](../standard-library/steady-clock-struct.md)
