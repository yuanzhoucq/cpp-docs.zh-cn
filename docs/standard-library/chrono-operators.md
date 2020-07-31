---
title: '&lt;chrono&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 82f0b7b0f55cf4d71ef7c0ed92a55ca0fa1139e0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230138"
---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt; 运算符

## <a name="operator-"></a><a name="operator-"></a>操作员

用于对 [duration](../standard-library/duration-class.md) 和 [time_point](../standard-library/time-point-class.md) 对象进行减法或求反运算的运算符。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator-(
       const duration<Rep1, Period1>& Left,
       cconst duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type
   operator-(
       const time_point<Clock, Duration1>& Time,
       const duration<Rep2, Period2>& Dur);

template <class Clock, class Duration1, class Duration2>
constexpr typename common_type<Duration1, Duration2>::type
   operator-(
       const time_point<Clock, Duration1>& Left,
       const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>参数

*左中*\
左侧的 `duration` 或 `time_point` 对象。

*然后*\
右侧的 `duration` 或 `time_point` 对象。

*阶段*\
`time_point` 对象。

*工期*\
`duration` 对象。

### <a name="return-value"></a>返回值

第一个函数返回一个 `duration` 对象，其间隔长度是两个参数的时间间隔之差。

第二个函数返回一个 `time_point` 对象，该对象表示一个时间点，该时间点由 "*工期*" 指定的时间间隔（从 "*时间*" 指定的时间点）中被替换。

第三个函数返回一个 `duration` 对象，该对象表示*左右*两个*Right*时间间隔。

## <a name="operator"></a><a name="op_neq"></a>operator！ =

[duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 对象的不等运算符。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator!=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator!=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>参数

*左中*\
左侧的 `duration` 或 `time_point` 对象。

*然后*\
右侧的 `duration` 或 `time_point` 对象。

### <a name="return-value"></a>返回值

每个函数均返回 `!(Left == Right)`。

## <a name="operator"></a><a name="op_star"></a>操作员

[duration](../standard-library/chrono-operators.md#op_star) 对象的乘法运算符。

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator*(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Mult);

template <class Rep1, class Rep2, class Period2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period2>
   operator*(
       const Rep1& Mult,
       const duration<Rep2,
       Period2>& Dur);
```

### <a name="parameters"></a>参数

*工期*\
`duration` 对象。

*Mult*\
一个整数值。

### <a name="return-value"></a>返回值

每个函数返回一个 `duration` 对象，其间隔长度为*Mult*乘以 "*工期*" 的长度。

除非 `is_convertible<Rep2, common_type<Rep1, Rep2>>`*“保持为 true”*，否则第一个函数不参与重载决策。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。

除非 `is_convertible<Rep1, common_type<Rep1, Rep2>>`*“保持为 true”*，否则第二个函数不参与重载决策。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。

## <a name="operator"></a><a name="op_div"></a>操作员

[duration](../standard-library/chrono-operators.md#op_star) 对象的除法运算符。

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator/(
     const duration<Rep1, Period1>& Dur,
     const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<Rep1, Rep2>::type
   operator/(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>参数

*工期*\
`duration` 对象。

*V*\
一个整数值。

*左中*\
左 `duration` 对象。

*然后*\
正确的 `duration` 对象。

### <a name="return-value"></a>返回值

第一个运算符返回持续时间对象，其间隔长度为按值*Div**除以的*值的长度。

第二个运算符返回*左*和*右*的间隔长度的比率。

除非 `is_convertible<Rep2, common_type<Rep1, Rep2>>`*“保持为 true”*，并且 `Rep2` 不是 `duration` 的实例化，否则第一个运算符不参与重载决策。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。

## <a name="operator"></a><a name="op_add"></a>operator +

添加 [duration](../standard-library/duration-class.md) 和 [time_point](../standard-library/time-point-class.md) 对象。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator+(
      const duration<Rep1, Period1>& Left,
      const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type>
   operator+(
      const time_point<Clock, Duration1>& Time,
      const duration<Rep2, Period2>& Dur);

template <class Rep1, class Period1, class Clock, class Duration2>
time_point<Clock, constexpr typename common_type<duration<Rep1, Period1>, Duration2>::type>
   operator+(
      const duration<Rep1, Period1>& Dur,
      const time_point<Clock, Duration2>& Time);
```

### <a name="parameters"></a>参数

*左中*\
左侧的 `duration` 或 `time_point` 对象。

*然后*\
右侧的 `duration` 或 `time_point` 对象。

*阶段*\
`time_point` 对象。

*工期*\
`duration` 对象。

### <a name="return-value"></a>返回值

第一个函数返回一个 `duration` 对象，该对象的时间间隔等于*左右*间隔之和。 *Right*

第二个和第三个函数返回一个 `time_point` 对象，该对象表示从时间点开始被替换*Dur*的时间点。 *Time*

## <a name="operatorlt"></a><a name="op_lt"></a>操作员&lt;

确定一个 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 对象是否小于另一个 `duration` 或 `time_point` 对象。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>参数

*左中*\
左侧的 `duration` 或 `time_point` 对象。

*然后*\
右侧的 `duration` 或 `time_point` 对象。

### <a name="return-value"></a>返回值

**`true`** 如果*左侧*的间隔长度小于*右*的间隔长度，则第一个函数返回。 否则，该函数将返回 **`false`** 。

**`true`** 如果*靠左* *，则*第二个函数返回。 否则，该函数将返回 **`false`** 。

## <a name="operatorlt"></a><a name="op_lt_eq"></a>操作员&lt;=

确定一个 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 对象是否小于或等于另一个 `duration` 或 `time_point` 对象。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>参数

*左中*\
左侧的 `duration` 或 `time_point` 对象。

*然后*\
右侧的 `duration` 或 `time_point` 对象。

### <a name="return-value"></a>返回值

每个函数均返回 `!(Right < Left)`。

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

确定两个 `duration` 对象是否表示相同长度的时间间隔，或两个 `time_point` 对象是否表示相同的时间点。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator==(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator==(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>参数

*左中*\
左侧的 `duration` 或 `time_point` 对象。

*然后*\
右侧的 `duration` 或 `time_point` 对象。

### <a name="return-value"></a>返回值

**`true`** 如果*左侧*和*右侧*表示具有相同长度的时间间隔，则第一个函数返回。 否则，该函数将返回 **`false`** 。

**`true`** 如果*左侧*和*右侧*表示相同的时间点，则第二个函数返回。 否则，该函数将返回 **`false`** 。

## <a name="operatorgt"></a><a name="op_gt"></a>操作员&gt;

确定一个 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 对象是否大于另一个 `duration` 或 `time_point` 对象。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>参数

*左中*\
左侧的 `duration` 或 `time_point` 对象。

*然后*\
右侧的 `duration` 或 `time_point` 对象。

### <a name="return-value"></a>返回值

每个函数均返回 `Right < Left`。

## <a name="operatorgt"></a><a name="op_gt_eq"></a>操作员&gt;=

确定一个 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 对象是否大于或等于另一个 `duration` 或 `time_point` 对象。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>参数

*左中*\
左侧的 `duration` 或 `time_point` 对象。

*然后*\
右侧的 `duration` 或 `time_point` 对象。

### <a name="return-value"></a>返回值

每个函数均返回 `!(Left < Right)`。

## <a name="operator-modulo"></a><a name="op_modulo"></a>运算符取模

用于对 [duration](../standard-library/duration-class.md) 对象进行取模操作的运算符。

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<Rep1, Period1, Rep2>::type
   operator%(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, _Period1>, duration<Rep2, Period2>>::type
   operator%(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>参数

*工期*\
`duration` 对象。

*V*\
一个整数值。

*左中*\
左 `duration` 对象。

*然后*\
正确的 `duration` 对象。

### <a name="return-value"></a>返回值

第一个函数返回一个 `duration` 对象，其间隔长度为 "*工期*模数" *Div*。

第二个函数返回一个值，该值表示*左*取模*向右*。
