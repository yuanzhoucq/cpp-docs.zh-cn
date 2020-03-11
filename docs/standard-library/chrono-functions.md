---
title: '&lt;chrono&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
ms.openlocfilehash: 85fdd413354b3f310d3315a80cf7da983cf6621d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865189"
---
# <a name="ltchronogt-functions"></a>&lt;chrono&gt; 函数

## <a name="duration_cast"></a>duration_cast

将 `duration` 对象转换为指定类型。

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);

template <class ToDuration, class Rep, class Period>
constexpr ToDuration floor(const duration<Rep, Period>& d);
template <class ToDuration, class Rep, class Period>
constexpr ToDuration ceil(const duration<Rep, Period>& d);
template <class ToDuration, class Rep, class Period>
constexpr ToDuration round(const duration<Rep, Period>& d);
```

### <a name="return-value"></a>返回值

一个表示时间间隔 `duration` 的 `To` 类型的 `Dur` 对象，需进行截断才能适应目标类型大小。

### <a name="remarks"></a>备注

如果 `To` 为 `duration` 的实例化，则此函数不参与重载决策。

## <a name="time_point_cast"></a>time_point_cast

将 [time_point](../standard-library/time-point-class.md) 对象转换为指定类型。

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);

template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
floor(const time_point<Clock, Duration>& tp);
template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
ceil(const time_point<Clock, Duration>& tp);
template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
round(const time_point<Clock, Duration>& tp);
```

### <a name="return-value"></a>返回值

持续时间为 `time_point` 类型的 `To` 对象。

### <a name="remarks"></a>备注

除非 `To` 为 [duration](../standard-library/duration-class.md) 的实例化，否则函数不参与重载决策。
