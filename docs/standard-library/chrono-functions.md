---
title: '&lt;chrono&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
ms.openlocfilehash: 5aadf776cc25e22a40ed75f854481dff63cce4bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371644"
---
# <a name="ltchronogt-functions"></a>&lt;chrono&gt; 函数

||||
|-|-|-|
|[duration_cast](#duration_cast)|[time_point_cast](#time_point_cast)|

## <a name="duration_cast"></a>  duration_cast

将 `duration` 对象转换为指定类型。

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);
```

### <a name="return-value"></a>返回值

一个表示时间间隔 `Dur` 的 `To` 类型的 `duration` 对象，需进行截断才能适应目标类型大小。

### <a name="remarks"></a>备注

如果 `To` 为 `duration` 的实例化，则此函数不参与重载决策。

## <a name="time_point_cast"></a>  time_point_cast

将 [time_point](../standard-library/time-point-class.md) 对象转换为指定类型。

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);
```

### <a name="return-value"></a>返回值

持续时间为 `To` 类型的 `time_point` 对象。

### <a name="remarks"></a>备注

除非 `To` 为 [duration](../standard-library/duration-class.md) 的实例化，否则函数不参与重载决策。

## <a name="see-also"></a>请参阅

[\<chrono>](../standard-library/chrono.md)<br/>
