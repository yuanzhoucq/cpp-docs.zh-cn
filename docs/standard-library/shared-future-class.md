---
title: shared_future 类
ms.date: 11/04/2016
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.openlocfilehash: 65ea01a9ced1ca69cd1b1526e7594c4b54387553
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336784"
---
# <a name="shared_future-class"></a>shared_future 类

描述*异步返回对象*。 相较于 [future](../standard-library/future-class.md) 对象，*异步提供程序* 可与任意数量的 `shared_future` 对象关联。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>备注

不要调用除以下项之外的任何方法：`valid`、`operator=` 和为空** 的 `shared_future` 对象上的析构函数。

也不要同步 `shared_future` 对象。 从多个线程调用同一个对象上的方法，这会引发不可预知的结果。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[shared_future](#shared_future)|构造 `shared_future` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[get](#get)|检索存储在*关联异步状态*中的结果。|
|[有效](#valid)|指定对象是否不为空。|
|[等](#wait)|阻止当前线程，直到关联异步状态为准备就绪。|
|[wait_for](#wait_for)|进行阻止，直到关联异步状态为准备就绪或已过指定时间。|
|[wait_until](#wait_until)|进行阻止，直到关联异步状态为准备就绪或直到指定时间点。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[shared_future：：操作员*](#op_eq)|分配新的关联异步状态。|

## <a name="requirements"></a>要求

**标题：**\<未来>

**命名空间:** std

## <a name="shared_futureget"></a><a name="get"></a>shared_future：获取

检索存储在*关联异步状态*中的结果。

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>备注

如果结果为异常，该方法将重新引发它。 否则，会返回结果。

在检索结果前，该方法会阻止当前线程，直到关联异步状态为准备就绪。

对于部分专用化 `shared_future<Ty&>`，存储值实际上是对已传递给*异步提供程序*作为返回值的对象的引用。

由于专门化`shared_future<void>`不存在存储值，因此该方法返回**空**值。

## <a name="shared_futureoperator"></a><a name="op_eq"></a>shared_future：：操作员*

从*指定对象传输关联异步状态*。

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>参数

*对*\
`shared_future` 对象。

### <a name="return-value"></a>返回值

`*this`

### <a name="remarks"></a>备注

对于第一个运算符 *，Right*在操作后不再具有关联的异步状态。

对于第二种方法 *，Right*保持其关联的异步状态。

## <a name="shared_futureshared_future-constructor"></a><a name="shared_future"></a>shared_future：shared_future构造函数

构造 `shared_future` 对象。

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>参数

*对*\
一个 [future](../standard-library/future-class.md) 或 一个 `shared_future` 对象。

### <a name="remarks"></a>备注

第一个构造函数构造没有关联异步状态** 的 `shared_future` 对象。

第二个和第三个构造函数构造`shared_future`一个对象并从*右*传输关联的异步状态。 *右*不再具有关联的异步状态。

第四个构造函数构造一`shared_future`个与*右*具有相同关联异步状态的对象。

## <a name="shared_futurevalid"></a><a name="valid"></a>shared_future：有效

指定对象是否具有关联异步状态**。

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>返回值

如果对象具有关联的异步状态，**则为 true;** 否则，**假**。

## <a name="shared_futurewait"></a><a name="wait"></a>shared_future：：等待

阻止当前线程，直到*关联的异步状态**准备就绪*。

```cpp
void wait() const;
```

### <a name="remarks"></a>备注

只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会为准备就绪。

## <a name="shared_futurewait_for"></a><a name="wait_for"></a>shared_future：wait_for

阻止当前线程，直到关联异步状态为准备就绪** 或已过指定时间。

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>参数

*Rel_time*\
一个 [chrono::duration](../standard-library/duration-class.md) 对象，指定线程阻止的最大时间间隔。

### <a name="return-value"></a>返回值

一个 [future_status](../standard-library/future-enums.md#future_status)，指示返回的原因。

### <a name="remarks"></a>备注

只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会为准备就绪**。

## <a name="shared_futurewait_until"></a><a name="wait_until"></a>shared_future：wait_until

阻止当前线程，直到关联的异步状态为准备就绪** 或直到指定时间点后。

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>参数

*Abs_time*\
一个 [chrono::time_point](../standard-library/time-point-class.md) 对象，指定在其后可取消阻止线程的时间。

### <a name="return-value"></a>返回值

一个 [future_status](../standard-library/future-enums.md#future_status)，指示返回的原因。

### <a name="remarks"></a>备注

只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会为准备就绪。

## <a name="see-also"></a>另请参阅

[标题文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<未来>](../standard-library/future.md)
