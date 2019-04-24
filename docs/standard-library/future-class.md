---
title: future 类
ms.date: 11/04/2016
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.openlocfilehash: 9ca18e62038d93a50b592868f71223962a22857d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159322"
---
# <a name="future-class"></a>future 类

描述异步返回对象。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>备注

每个标准*异步提供程序*返回一个对象，该对象的类型是此模板的实例化。 `future` 对象提供与其关联的异步提供程序的唯一访问权限。 如需多个与同一异步提供程序关联的异步返回对象，请将 `future` 对象复制到 [shared_future](../standard-library/shared-future-class.md) 对象。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[future](#future)|构造 `future` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[get](#get)|检索存储在关联异步状态中的结果。|
|[share](#share)|将对象转换为 `shared_future`。|
|[valid](#valid)|指定对象是否不为空。|
|[wait](#wait)|阻止当前线程，直到关联异步状态为准备就绪。|
|[wait_for](#wait_for)|进行阻止，直到关联异步状态为准备就绪或已过指定时间。|
|[wait_until](#wait_until)|进行阻止，直到关联异步状态为准备就绪或直到指定时间点。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[future::operator=](#op_eq)|从指定对象传输关联异步状态。|

## <a name="requirements"></a>要求

**标头：** \<将来 >

**命名空间：** std

## <a name="future"></a>future::future 构造函数

构造 `future` 对象。

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>参数

*其他*<br/>
一个 `future` 对象。

### <a name="remarks"></a>备注

第一个构造函数构造没有关联异步状态的 `future` 对象。

第二个构造函数构造`future`对象，并传输关联异步状态从*其他*。 *其他*不再具有关联异步状态。

## <a name="get"></a>future::get

检索存储在关联异步状态中的结果。

```cpp
Ty get();
```

### <a name="return-value"></a>返回值

如果结果为异常，该方法将重新引发它。 否则，会返回结果。

### <a name="remarks"></a>备注

在检索结果前，该方法会阻止当前线程，直到关联异步状态为准备就绪。

对于部分专用化 `future<Ty&>`，存储值实际上是对已传递给异步提供程序作为返回值的对象的引用。

因为对于专用化不存在任何存储的值`future<void>`，该方法将返回**void**。

在其他专用化中，此方法会从存储值移动其返回值。 因此，请仅调用此方法一次。

## <a name="op_eq"></a>future::operator=

从指定对象传输关联异步状态。

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>参数

右侧<br/>
一个 `future` 对象。

### <a name="return-value"></a>返回值

`*this`

### <a name="remarks"></a>备注

传输后，*右*不再具有关联异步状态。

## <a name="share"></a>future::share

将对象转换为 [shared_future](../standard-library/shared-future-class.md) 对象。

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>返回值

`shared_future(move(*this))`

## <a name="valid"></a>future::valid

指定对象是否具有关联异步状态。

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>返回值

**true**如果该对象具有关联异步状态; 否则为**false**。

## <a name="wait"></a>future::wait

阻止当前线程，直到关联异步状态为准备就绪。

```cpp
void wait() const;
```

### <a name="remarks"></a>备注

只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会为准备就绪。

## <a name="wait_for"></a>future::wait_for

阻止当前线程，直到关联异步状态为准备就绪或已过指定时间间隔。

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>参数

*Rel_time*<br/>
一个 [chrono::duration](../standard-library/duration-class.md) 对象，指定线程阻止的最大时间间隔。

### <a name="return-value"></a>返回值

一个 [future_status](../standard-library/future-enums.md#future_status)，指示返回的原因。

### <a name="remarks"></a>备注

只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会为准备就绪。

## <a name="wait_until"></a>future::wait_until

阻止当前线程，直到关联的异步状态为准备就绪或直到指定时间点后。

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>参数

*Abs_time*<br/>
一个 [chrono::time_point](../standard-library/time-point-class.md) 对象，指定在其后可取消阻止线程的时间。

### <a name="return-value"></a>返回值

一个 [future_status](../standard-library/future-enums.md#future_status)，指示返回的原因。

### <a name="remarks"></a>备注

只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会为准备就绪。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
