---
title: completion_future 类
ms.date: 11/04/2016
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
ms.openlocfilehash: 1863f0908753fb05abb01cf1bd2e34dc6649e0a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228487"
---
# <a name="completion_future-class"></a>completion_future 类

表示与 C++ AMP 异步操作对应的将来。

## <a name="syntax"></a>语法

```cpp
class completion_future;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[completion_future 构造函数](#ctor)|初始化 `completion_future` 类的新实例。|
|[~ completion_future 析构函数](#dtor)|销毁 `completion_future` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[get](#get)|等待，直到关联的异步操作完成。|
|[接着](#then)|将回调函数对象链接到在 `completion_future` 关联的异步操作完成执行时要执行的对象。|
|[to_task](#to_task)|返回 `task` 对应于关联的异步操作的对象。|
|[适用](#valid)|获取一个布尔值，该值指示对象是否与异步操作关联。|
|[再](#wait)|阻止，直到关联的异步操作完成。|
|[wait_for](#wait_for)|阻止，直到关联的异步操作完成或指定的时间 `_Rel_time` 已过。|
|[wait_until](#wait_until)|阻止，直到关联的异步操作完成或当前时间超过指定的值为止 `_Abs_time` 。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[运算符 std：： shared_future\<void>](#operator_shared_future)|将对象隐式转换 `completion_future` 为 `std::shared_future` 对象。|
|[operator =](#operator_eq)|将指定对象的内容复制 `completion_future` 到此对象中。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`completion_future`

## <a name="requirements"></a>要求

**标头：** amprt

**命名空间：** 并发

## <a name="completion_future"></a><a name="ctor"></a>completion_future

初始化 `completion_future` 类的新实例。

### <a name="syntax"></a>语法

```cpp
completion_future();

completion_future(
    const completion_future& _Other );

completion_future(
    completion_future&& _Other );
```

### <a name="parameters"></a>参数

*_Other*<br/>
要复制或移动的 `completion_future` 对象。

### <a name="overloads-list"></a>重载列表

|名称|说明|
|----------|-----------------|
|`completion_future();`|初始化 `completion_future` 类的新实例。|
|`completion_future(const completion_future& _Other);`|通过复制构造函数来初始化 `completion_future` 类的新实例。|
|`completion_future(completion_future&& _Other);`|通过移动构造函数来初始化 `completion_future` 类的新实例。|

## <a name="get"></a><a name="get"></a>获取

等待，直到关联的异步操作完成。 如果在异步操作时遇到存储的异常，则将引发该异常。

### <a name="syntax"></a>语法

```cpp
void get() const;
```

## <a name="operator-stdshared_futurevoid"></a><a name="operator_shared_future"></a>运算符 std：： shared_future\<void>

将对象隐式转换 `completion_future` 为 `std::shared_future` 对象。

### <a name="syntax"></a>语法

```cpp
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>返回值

一个 `std::shared_future` 对象。

## <a name="operator"></a><a name="operator_eq"></a>operator =

将指定对象的内容复制 `completion_future` 到此对象中。

### <a name="syntax"></a>语法

```cpp
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>参数

*_Other*<br/>
从其中复制的对象。

### <a name="return-value"></a>返回值

对此对象的引用 `completion_future` 。

## <a name="overloads-list"></a>重载列表

|名称|说明|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|使用深层复制将指定 `completion_future` 对象的内容复制到此对象中。|
|`completion_future& operator=(completion_future&& _Other);`|使用移动赋值将指定 `completion_future` 对象的内容复制到此对象中。|

## <a name="then"></a><a name="then"></a>接着

将回调函数对象链接到在 `completion_future` 关联的异步操作完成执行时要执行的对象。

### <a name="syntax"></a>语法

```cpp
template <typename _Functor>
void then(const _Functor & _Func ) const;
```

### <a name="parameters"></a>参数

*_Functor*<br/>
回调函子。

*_Func*<br/>
回调函数对象。

## <a name="to_task"></a><a name="to_task"></a>to_task

返回 `task` 对应于关联的异步操作的对象。

### <a name="syntax"></a>语法

```cpp
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>返回值

对应于关联的异步操作的 `task` 对象。

## <a name="valid"></a><a name="valid"></a>适用

获取一个布尔值，指示该对象是否与异步操作关联。

### <a name="syntax"></a>语法

```cpp
bool valid() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果对象与异步操作关联，则为; 否则为。否则为 **`false`** 。

## <a name="wait"></a><a name="wait"></a>再

阻止，直到关联的异步操作完成。

### <a name="syntax"></a>语法

```cpp
void wait() const;
```

## <a name="wait_for"></a><a name="wait_for"></a>wait_for

阻止，直到关联的异步操作完成或指定的时间 `_Rel_time` 已过。

### <a name="syntax"></a>语法

```cpp
template <
    class _Rep,
    class _Period
>
std::future_status::future_status wait_for(
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;
```

### <a name="parameters"></a>参数

*_Rep*<br/>
表示计时周期数的算术类型。

*_Period*<br/>
Std：：比率，表示每个时钟周期所经过的秒数。

*_Rel_time*<br/>
等待操作完成的最长时间。

### <a name="return-value"></a>返回值

返回：

- `std::future_status::deferred`如果关联的异步操作未运行，则为。

- `std::future_status::ready`如果关联的异步操作已完成，则为。

- `std::future_status::timeout`如果已过指定的时间段。

## <a name="wait_until"></a><a name="wait_until"></a>wait_until

阻止，直到关联的异步操作完成或当前时间超过指定的值为止 `_Abs_time` 。

### <a name="syntax"></a>语法

```cpp
template <
    class _Clock,
    class _Duration
>
std::future_status::future_status wait_until(
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;
```

### <a name="parameters"></a>参数

*_Clock*<br/>
测量此时间点的时钟。

*_Duration*<br/>
自开始 epoch 以来的时间间隔，在此时间段 `_Clock` 后，函数将超时。

*_Abs_time*<br/>
函数将在该时间点超时的时间点。

### <a name="return-value"></a>返回值

返回：

1. `std::future_status::deferred`如果关联的异步操作未运行，则为。

1. `std::future_status::ready`如果关联的异步操作已完成，则为。

1. `std::future_status::timeout`如果指定的时间段已过去。

## <a name="completion_future"></a><a name="dtor"></a>~ completion_future

销毁 `completion_future` 对象。

### <a name="syntax"></a>语法

```cpp
~completion_future();
```

## <a name="see-also"></a>另请参阅

[并发命名空间（C++ AMP）](concurrency-namespace-cpp-amp.md)
