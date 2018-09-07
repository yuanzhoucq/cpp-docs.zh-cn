---
title: duration 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
dev_langs:
- C++
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::chrono [C++], duration
ms.workload:
- cplusplus
ms.openlocfilehash: bb4d2c813b53a180f13d5047dc0d78dae98fe59f
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100906"
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
|[持续时间](#duration)|构造 `duration` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[count](#count)|返回时间间隔内的时钟计时周期数。|
|[max](#max)|静态。 返回模板参数 `Ref` 的最大允许值。|
|[min](#min)|静态。 返回模板参数 `Ref` 的最低允许值。|
|[零](#zero)|静态。 实际返回 `Rep`(0)。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[duration::operator-](#operator-)|返回 `duration` 对象的副本及求反后的计时周期计数。|
|[duration::operator--](#operator--)|减小存储的计时周期计数。|
|[duration::operator=](#op_eq)|将存储的计时周期计数取模减少指定值。|
|[duration::operator*=](#op_star_eq)|将存储的计时周期计数乘以指定值。|
|[duration::operator/=](#op_div_eq)|将存储的计时周期计数除以指定的 `duration` 对象的计时周期计数。|
|[duration::operator+](#op_add)|返回 `*this`。|
|[duration::operator++](#op_add_add)|增加存储的计时周期计数。|
|[duration::operator+=](#op_add_eq)|将存储的计时周期计数加上指定的 `duration` 对象的计时周期计数。|
|[duration::operator-=](#operator-_eq)|从存储的计时周期计数减去指定的 `duration` 对象的计时周期计数。|

## <a name="requirements"></a>要求

**标头：** \<chrono >

**命名空间：** std::chrono

## <a name="count"></a>  duration::count

检索时间间隔内的时钟计时周期数。

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>返回值

时间间隔内的时钟计时周期数。

## <a name="duration"></a>  duration::duration 构造函数

构造 `duration` 对象。

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);


template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>参数

*Rep2*<br/>
表示计时周期数的算术类型。

*Period2*<br/>
表示以秒为单位的计时周期时间段的 `std::ratio` 专用模板。

*R*<br/>
默认时间段的计时周期数。

*Dur*<br/>
指定的时间段的计时周期数*Period2*。

### <a name="remarks"></a>备注

默认构造函数构造未经初始化的对象。 通过使用空大括号进行的值初始化会初始化表示零个时钟计时周期的时间间隔的对象。

第二个、 一个模板参数构造函数将构造一个对象，表示的时间间隔*R*时钟计时周期使用的默认时间段的`std::ratio<1>`。 若要避免舍的滴答计数，则返回错误，构造一个持续时间对象从一种表示类型*Rep2* ，可将其视为浮点类型`duration::rep`不能被视为浮点类型。

第三，两个模板参数构造函数将构造一个对象，表示时间间隔，其长度是由指定的时间间隔*Dur*。 若要避免计时周期计数截断，从另一个其类型与目标类型之间为*不可公度*的持续时间对象构造一个持续时间对象这一做法是错误的。

如果不能将 `D2` 视为浮点类型且 [ratio_divide\<D1::period, D2::period>::type::den](../standard-library/ratio.md) 不是 1，持续时间类型 `D1` 与其他持续时间类型 `D2` *不可公度*。

除非*Rep2*隐式转换为`rep`并将`treat_as_floating_point<rep>`*如此*或`treat_as_floating_point<Rep2>` *false*，第二个构造函数不参与重载决策。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。

除非转换中没有引发溢出且 `treat_as_floating_point<rep>` *为 true*，或 `ratio_divide<Period2, period>::den` 等于 1 且 `treat_as_floating_point<Rep2>` *为 false*，否则第三个构造函数将不参与重载决策。 有关详细信息，请参阅 [<type_traits>](../standard-library/type-traits.md)。

## <a name="max"></a>  duration::max

返回模板参数类型 `Ref` 的值上限的静态方法。

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>返回值

实际上，返回 `duration(duration_values<rep>::max())`。

## <a name="min"></a>  duration::min

返回模板参数类型 `Ref` 的值下限的静态方法。

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>返回值

实际上，返回 `duration(duration_values<rep>::min())`。

## <a name="duration__operator-"></a>  duration::operator-

返回 `duration` 对象的副本及求反后的计时周期计数。

```cpp
constexpr duration operator-() const;
```

## <a name="duration__operator--"></a>  duration::operator--

减小存储的计时周期计数。

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>返回值

第一种方法返回 `*this`。

第二种方法返回递减之前生成的 `*this` 副本。

## <a name="op_eq"></a>  duration::operator=

将存储的计时周期计数取模减少指定值。

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>参数

*Div*<br/>
对于第一个方法，请*Div*表示的计时周期计数。 对于第二个方法，请*Div*是`duration`对象，其中包含的计时周期计数。

### <a name="return-value"></a>返回值

执行取模操作后的 `duration` 对象。

## <a name="op_star_eq"></a>  duration::operator*=

将存储的计时周期计数乘以指定值。

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>参数

*Mult*<br/>
`duration::rep` 指定的类型的值。

### <a name="return-value"></a>返回值

执行相乘后的 `duration` 对象。

## <a name="op_div_eq"></a>  duration::operator/=

将存储的计时周期计数除以指定值。

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>参数

*Div*<br/>
`duration::rep` 指定的类型的值。

### <a name="return-value"></a>返回值

执行相除后的 `duration` 对象。

## <a name="op_add"></a>  duration::operator+

返回 `*this`。

```cpp
constexpr duration operator+() const;
```

## <a name="op_add_add"></a>  duration::operator++

增加存储的计时周期计数。

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>返回值

第一种方法返回 `*this`。

第二种方法返回递增前生成的 `*this` 副本。

## <a name="op_add_eq"></a>  duration::operator+=

将存储的计时周期计数加上指定的 `duration` 对象的计时周期计数。

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>参数

*Dur*<br/>
一个 `duration` 对象。

### <a name="return-value"></a>返回值

执行相加后的 `duration` 对象。

## <a name="duration__operator-_eq"></a>  duration::operator-=

从存储的计时周期计数减去指定的 `duration` 对象的计时周期计数。

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>参数

*Dur*<br/>
一个 `duration` 对象。

### <a name="return-value"></a>返回值

执行相减后的 `duration` 对象。

## <a name="zero"></a>  duration::zero

返回 `duration(duration_values<rep>::zero())`。

```cpp
static constexpr duration zero();
```

## <a name="op_mod_eq"></a>  duration::operator mod=

减少存储的滴答计数取模 Div 或 Div.count()。

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>参数

*Div*<br/>
除数是表示滴答计数的 duration 对象或值。

### <a name="remarks"></a>备注

第一个成员函数将减少存储的滴答计数取模 Div 并返回 *this。 第二个成员函数将减少存储的计时周期计数取模 Div.count() 并返回 \*this。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[duration_values 结构](../standard-library/duration-values-structure.md)<br/>
