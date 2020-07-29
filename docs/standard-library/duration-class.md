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
ms.openlocfilehash: 454c03aeb1a4666543a28759d02405a512453ffc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217787"
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

|名称|描述|
|----------|-----------------|
|duration::period Typedef|表示模板参数 `Period` 的同义词。|
|duration::rep Typedef|表示模板参数 `Rep` 的同义词。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[duration](#duration)|构造 `duration` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[计数](#count)|返回时间间隔内的时钟计时周期数。|
|[max](#max)|静态。 返回模板参数 `Ref` 的最大允许值。|
|[min](#min)|静态。 返回模板参数 `Ref` 的最低允许值。|
|[无](#zero)|静态。 实际返回 `Rep`(0)。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[duration：： operator-](#operator-)|返回 `duration` 对象的副本及求反后的计时周期计数。|
|[duration：： operator--](#operator--)|减小存储的计时周期计数。|
|[duration：： operator =](#op_eq)|将存储的计时周期计数取模减少指定值。|
|[duration：： operator * =](#op_star_eq)|将存储的计时周期计数乘以指定值。|
|[duration：： operator/=](#op_div_eq)|将存储的计时周期计数除以指定的 `duration` 对象的计时周期计数。|
|[duration：： operator +](#op_add)|返回 **`*this`** 。|
|[duration：： operator + +](#op_add_add)|增加存储的计时周期计数。|
|[duration：： operator + =](#op_add_eq)|将存储的计时周期计数加上指定的 `duration` 对象的计时周期计数。|
|[duration：： operator-=](#operator-_eq)|从存储的计时周期计数减去指定的 `duration` 对象的计时周期计数。|

## <a name="requirements"></a>要求

**标头：**\<chrono>

**命名空间：** std::chrono

## <a name="durationcount"></a><a name="count"></a>duration：： count

检索时间间隔内的时钟计时周期数。

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>返回值

时间间隔内的时钟计时周期数。

## <a name="durationduration-constructor"></a><a name="duration"></a>持续时间：:d u 构造函数

构造 `duration` 对象。

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>参数

*Rep2*\
表示计时周期数的算术类型。

*Period2*\
表示以秒为单位的计时周期时间段的 `std::ratio` 专用模板。

*迅驰*\
默认时间段的计时周期数。

*工期*\
*Period2*指定的时间段的计时周期数。

### <a name="remarks"></a>备注

默认构造函数构造未经初始化的对象。 通过使用空大括号进行的值初始化会初始化表示零个时钟计时周期的时间间隔的对象。

第二，一个模板参数构造函数构造一个对象，该对象表示使用的默认时间段的*R*时钟计时周期的时间间隔 `std::ratio<1>` 。 若要避免刻度计数的舍入，从表示类型*Rep2*构造持续时间对象的错误是错误的，当不能将其视为浮点类型时，可以将该对象视为浮点类型 `duration::rep` 。

第三，两个模板参数构造函数构造一个对象，该对象表示时间间隔，其长度是由*工期*指定的时间间隔。 若要避免计时周期计数截断，从另一个其类型与目标类型之间为*不可公度*的持续时间对象构造一个持续时间对象这一做法是错误的。

`D1`如果无法将持续*incommensurable*时间类型 `D2` `D2` 视为浮点类型并且[ratio_divide \<D1::period, D2::period> ：： type：:d en](../standard-library/ratio.md)不是1，则持续时间类型为公度。

除非*Rep2*可隐式转换为 `rep` 且为 `treat_as_floating_point<rep>` *true*或 `treat_as_floating_point<Rep2>` *保留为 false*，否则第二个构造函数不参与重载决策。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。

除非转换中没有引发溢出且 `treat_as_floating_point<rep>`*为 true*，或 `ratio_divide<Period2, period>::den` 等于 1 且 `treat_as_floating_point<Rep2>`*为 false*，否则第三个构造函数将不参与重载决策。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。

## <a name="durationmax"></a><a name="max"></a>duration：： max

返回模板参数类型 `Ref` 的值上限的静态方法。

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>返回值

实际上，返回 `duration(duration_values<rep>::max())`。

## <a name="durationmin"></a><a name="min"></a>duration：： min

返回模板参数类型 `Ref` 的值下限的静态方法。

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>返回值

实际上，返回 `duration(duration_values<rep>::min())`。

## <a name="durationoperator-"></a><a name="operator-"></a>duration：： operator-

返回 `duration` 对象的副本及求反后的计时周期计数。

```cpp
constexpr duration operator-() const;
```

## <a name="durationoperator--"></a><a name="operator--"></a>duration：： operator--

减小存储的计时周期计数。

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>返回值

第一种方法返回 **`*this`** 。

第二种方法返回在 **`*this`** 减量之前创建的的副本。

## <a name="durationoperator"></a><a name="op_eq"></a>duration：： operator =

将存储的计时周期计数取模减少指定值。

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>参数

*V*\
对于第一种方法， *Div*表示滴答计数。 对于第二种方法， *Div*是 `duration` 包含滴答计数的对象。

### <a name="return-value"></a>返回值

执行取模操作后的 `duration` 对象。

## <a name="durationoperator"></a><a name="op_star_eq"></a>duration：： operator * =

将存储的计时周期计数乘以指定值。

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>参数

*Mult*\
`duration::rep` 指定的类型的值。

### <a name="return-value"></a>返回值

执行相乘后的 `duration` 对象。

## <a name="durationoperator"></a><a name="op_div_eq"></a>duration：： operator/=

将存储的计时周期计数除以指定值。

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>参数

*V*\
`duration::rep` 指定的类型的值。

### <a name="return-value"></a>返回值

执行相除后的 `duration` 对象。

## <a name="durationoperator"></a><a name="op_add"></a>duration：： operator +

返回 **`*this`** 。

```cpp
constexpr duration operator+() const;
```

## <a name="durationoperator"></a><a name="op_add_add"></a>duration：： operator + +

增加存储的计时周期计数。

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>返回值

第一种方法返回 **`*this`** 。

第二个方法返回在 **`*this`** 增量之前所做的的副本。

## <a name="durationoperator"></a><a name="op_add_eq"></a>duration：： operator + =

将存储的计时周期计数加上指定的 `duration` 对象的计时周期计数。

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>参数

*工期*\
`duration` 对象。

### <a name="return-value"></a>返回值

执行相加后的 `duration` 对象。

## <a name="durationoperator-"></a><a name="operator-_eq"></a>duration：： operator-=

从存储的计时周期计数减去指定的 `duration` 对象的计时周期计数。

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>参数

*工期*\
`duration` 对象。

### <a name="return-value"></a>返回值

执行相减后的 `duration` 对象。

## <a name="durationzero"></a><a name="zero"></a>duration：：零

返回 `duration(duration_values<rep>::zero())`。

```cpp
static constexpr duration zero();
```

## <a name="durationoperator-mod"></a><a name="op_mod_eq"></a>duration：： operator mod =

减少存储的滴答计数取模 Div 或 Div.count()。

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>参数

*V*\
除数是表示滴答计数的 duration 对象或值。

### <a name="remarks"></a>备注

第一个成员函数将减少存储的滴答计数取模 Div 并返回 *this。 第二个成员函数将减少存储的计时周期计数取模 Div.count() 并返回 \*this。

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[duration_values 结构](../standard-library/duration-values-structure.md)
