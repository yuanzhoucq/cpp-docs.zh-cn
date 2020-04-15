---
title: duration 类
ms.date: 03/27/2016
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
helpviewer_keywords:
- std::chrono [C++], duration
ms.openlocfilehash: 3669935bf094f476ca24a8170a0388dff29e0a0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368755"
---
# <a name="duration-class"></a>duration 类

描述保存“*时间间隔*”（即两个时间点之间的运行时间）的类型。

## <a name="syntax"></a>语法

```cpp
template <class Rep, class Period = ratio<1>>
class duration;
template <class Rep, class Period>
class duration;
template <class Rep, class Period1, class Period2>
class duration <duration<Rep, Period1>, Period2>;
```

## <a name="remarks"></a>备注

模板参数 `Rep` 描述用于保存间隔中的时钟计时周期数的类型。 模板参数 `Period` 是描述每个计时周期所表示间隔的大小的[比率](../standard-library/ratio.md) 的实例化。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|duration::period Typedef|表示模板参数 `Period` 的同义词。|
|duration::rep Typedef|表示模板参数 `Rep` 的同义词。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[时间](#duration)|构造 `duration` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[count](#count)|返回时间间隔内的时钟计时周期数。|
|[麦克斯](#max)|静态。 返回模板参数 `Ref` 的最大允许值。|
|[分钟](#min)|静态。 返回模板参数 `Ref` 的最低允许值。|
|[零](#zero)|静态。 实际返回 `Rep`(0)。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[持续时间：：操作员-](#operator-)|返回 `duration` 对象的副本及求反后的计时周期计数。|
|[持续时间：：运算符--](#operator--)|减小存储的计时周期计数。|
|[持续时间：：操作员*](#op_eq)|将存储的计时周期计数取模减少指定值。|
|[持续时间：：操作员*](#op_star_eq)|将存储的计时周期计数乘以指定值。|
|[持续时间：：操作员/*](#op_div_eq)|将存储的计时周期计数除以指定的 `duration` 对象的计时周期计数。|
|[持续时间：：操作员*](#op_add)|返回 `*this`。|
|[持续时间：：操作员*](#op_add_add)|增加存储的计时周期计数。|
|[持续时间：：操作员*](#op_add_eq)|将存储的计时周期计数加上指定的 `duration` 对象的计时周期计数。|
|[持续时间：：操作员-*](#operator-_eq)|从存储的计时周期计数减去指定的 `duration` 对象的计时周期计数。|

## <a name="requirements"></a>要求

**标题：**\<计时>

**命名空间：** std::chrono

## <a name="durationcount"></a><a name="count"></a>持续时间：：计数

检索时间间隔内的时钟计时周期数。

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>返回值

时间间隔内的时钟计时周期数。

## <a name="durationduration-constructor"></a><a name="duration"></a>持续时间：:d构造函数

构造 `duration` 对象。

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>参数

*代表2*\
表示计时周期数的算术类型。

*期间2*\
表示以秒为单位的计时周期时间段的 `std::ratio` 专用模板。

*R*\
默认时间段的计时周期数。

*杜尔*\
*期间 2*指定的期间刻度数。

### <a name="remarks"></a>备注

默认构造函数构造未经初始化的对象。 通过使用空大括号进行的值初始化会初始化表示零个时钟计时周期的时间间隔的对象。

第二个模板参数构造函数构造一个对象，该对象使用 默认周期的*R*时钟刻度的时间间隔`std::ratio<1>`表示。 为了避免勾选计数的舍入，从表示类型*Rep2*构造持续时间对象是错误的，当不能被视为浮点类型时`duration::rep`，该对象可以被视为浮点类型。

第三个模板参数构造函数构造一个对象，该对象表示其长度为*Dur*指定的时间间隔的时间间隔。 若要避免计时周期计数截断，从另一个其类型与目标类型之间为*不可公度*的持续时间对象构造一个持续时间对象这一做法是错误的。

如果不能将 `D2` 视为浮点类型且 [ratio_divide\<D1::period, D2::period>::type::den](../standard-library/ratio.md) 不是 1，持续时间类型 `D1` 与其他持续时间类型 `D2`*不可公度*。

除非*Rep2*隐式`rep`可转换为`treat_as_floating_point<rep>`*，并且持有 true*或`treat_as_floating_point<Rep2>`*持有 false，* 否则第二个构造函数不参与重载解析。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。

除非转换中没有引发溢出且 `treat_as_floating_point<rep>`*为 true*，或 `ratio_divide<Period2, period>::den` 等于 1 且 `treat_as_floating_point<Rep2>`*为 false*，否则第三个构造函数将不参与重载决策。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。

## <a name="durationmax"></a><a name="max"></a>持续时间：最大

返回模板参数类型 `Ref` 的值上限的静态方法。

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>返回值

实际上，返回 `duration(duration_values<rep>::max())`。

## <a name="durationmin"></a><a name="min"></a>持续时间：：分钟

返回模板参数类型 `Ref` 的值下限的静态方法。

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>返回值

实际上，返回 `duration(duration_values<rep>::min())`。

## <a name="durationoperator-"></a><a name="operator-"></a>持续时间：：操作员-

返回 `duration` 对象的副本及求反后的计时周期计数。

```cpp
constexpr duration operator-() const;
```

## <a name="durationoperator--"></a><a name="operator--"></a>持续时间：：运算符--

减小存储的计时周期计数。

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>返回值

第一种方法返回 `*this`。

第二种方法返回递减之前生成的 `*this` 副本。

## <a name="durationoperator"></a><a name="op_eq"></a>持续时间：：操作员*

将存储的计时周期计数取模减少指定值。

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>参数

*Div*\
对于第一个方法 *，Div*表示刻度计数。 对于第二种方法 *，Div*是`duration`包含刻度计数的对象。

### <a name="return-value"></a>返回值

执行取模操作后的 `duration` 对象。

## <a name="durationoperator"></a><a name="op_star_eq"></a>持续时间：：操作员*

将存储的计时周期计数乘以指定值。

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>参数

*马尔特*\
`duration::rep` 指定的类型的值。

### <a name="return-value"></a>返回值

执行相乘后的 `duration` 对象。

## <a name="durationoperator"></a><a name="op_div_eq"></a>持续时间：：操作员/*

将存储的计时周期计数除以指定值。

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>参数

*Div*\
`duration::rep` 指定的类型的值。

### <a name="return-value"></a>返回值

执行相除后的 `duration` 对象。

## <a name="durationoperator"></a><a name="op_add"></a>持续时间：：操作员*

返回 `*this`。

```cpp
constexpr duration operator+() const;
```

## <a name="durationoperator"></a><a name="op_add_add"></a>持续时间：：操作员*

增加存储的计时周期计数。

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>返回值

第一种方法返回 `*this`。

第二种方法返回递增前生成的 `*this` 副本。

## <a name="durationoperator"></a><a name="op_add_eq"></a>持续时间：：操作员*

将存储的计时周期计数加上指定的 `duration` 对象的计时周期计数。

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>参数

*杜尔*\
`duration` 对象。

### <a name="return-value"></a>返回值

执行相加后的 `duration` 对象。

## <a name="durationoperator-"></a><a name="operator-_eq"></a>持续时间：：操作员-*

从存储的计时周期计数减去指定的 `duration` 对象的计时周期计数。

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>参数

*杜尔*\
`duration` 对象。

### <a name="return-value"></a>返回值

执行相减后的 `duration` 对象。

## <a name="durationzero"></a><a name="zero"></a>持续时间：：零

返回 `duration(duration_values<rep>::zero())`。

```cpp
static constexpr duration zero();
```

## <a name="durationoperator-mod"></a><a name="op_mod_eq"></a>持续时间：：运算符 mod*

减少存储的滴答计数取模 Div 或 Div.count()。

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>参数

*Div*\
除数是表示滴答计数的 duration 对象或值。

### <a name="remarks"></a>备注

第一个成员函数将减少存储的滴答计数取模 Div 并返回 *this。 第二个成员函数将减少存储的计时周期计数取模 Div.count() 并返回 \*this。

## <a name="see-also"></a>另请参阅

[标题文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[duration_values 结构](../standard-library/duration-values-structure.md)
