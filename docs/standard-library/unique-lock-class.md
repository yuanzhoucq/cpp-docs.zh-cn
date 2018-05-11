---
title: unique_lock 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::unique_lock
dev_langs:
- C++
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9888b847c3e52cd8b6a034e95e35ca73933acd3f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="uniquelock-class"></a>unique_lock 类

表示可进行实例化以创建管理 `mutex` 锁定和解锁的对象的模板。

## <a name="syntax"></a>语法

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>备注

模板参数 `Mutex` 必须命名为 mutex 类型。

在内部，`unique_lock` 存储一个指向关联的 `mutex` 对象的指针，以及一个指示当前线程是否拥有 `mutex` 的 `bool`。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`mutex_type`|模板参数 `Mutex` 的同义词。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[unique_lock](#unique_lock)|构造 `unique_lock` 对象。|
|[~unique_lock 析构函数](#dtorunique_lock_destructor)|释放与 `unique_lock` 对象关联的所有资源。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[lock](#lock)|阻止调用线程，直到线程获取关联的 `mutex` 的所有权。|
|[mutex](#mutex)|检索指向关联的 `mutex` 的存储指针。|
|[owns_lock](#owns_lock)|指定调用线程是否拥有关联的 `mutex`。|
|[release](#release)|解除 `unique_lock` 对象与关联的 `mutex` 对象的关联。|
|[swap](#swap)|将关联的 `mutex` 和所有权状态与指定对象的互换。|
|[try_lock](#try_lock)|在不阻止的情况下尝试获取关联 `mutex` 的所有权。|
|[try_lock_for](#try_lock_for)|在不阻止的情况下尝试获取关联 `mutex` 的所有权。|
|[try_lock_until](#try_lock_until)|在不阻止的情况下尝试获取关联 `mutex` 的所有权。|
|[unlock](#unlock)|释放关联的 `mutex` 的所有权。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator bool](#op_bool)|指定调用线程是否具有关联的 `mutex` 的所有权。|
|[operator=](#op_eq)|从指定对象复制存储的 `mutex` 指针和关联的所有权状态。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`unique_lock`

## <a name="requirements"></a>要求

**标头：** \<互斥体 >

**命名空间：** std

## <a name="lock"></a>lock

阻止调用线程，直到线程获取关联的 `mutex` 的所有权。

```cpp
void lock();
```

### <a name="remarks"></a>备注

如果存储的 `mutex` 指针为 `null`，则此方法将引发一个错误代码为 `operation_not_permitted` 的 [system_error](../standard-library/system-error-class.md)。

如果调用线程已拥有关联的 `mutex`，则此方法将引发一个错误代码为 `resource_deadlock_would_occur` 的 `system_error`。

否则，此方法将在关联的 `mutex` 上调用 `lock`，并将内部线程所有权标志设为 `true`。

## <a name="mutex"></a>  mutex

检索指向关联的 `mutex` 的存储指针。

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="op_bool"></a>operator bool

指定调用线程是否具有关联的 mutex 的所有权。

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>返回值

如果线程拥有 mutex，则为 `true`；否则为 `false`。

## <a name="op_eq"></a>operator=

从指定对象复制存储的 `mutex` 指针和关联的所有权状态。

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>参数

`Other` A`unique_lock`对象。

### <a name="return-value"></a>返回值

`*this`

### <a name="remarks"></a>备注

如果调用线程拥有以前关联的 `mutex`，则此方法在 `mutex` 上调用 `unlock` 之前，将分配新值。

复制后，此方法可将 `Other` 设为默认构造状态。

## <a name="owns_lock"></a>  owns_lock

指定调用线程是否拥有关联的 `mutex`。

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>返回值

如果线程拥有 `mutex`，则为 `true`；否则为 `false`。

## <a name="release"></a>  release

解除 `unique_lock` 对象与关联的 `mutex` 对象的关联。

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>返回值

存储的 `mutex` 指针的上一个值。

### <a name="remarks"></a>备注

此方法将存储的 `mutex` 指针的值设为 0，并将内部 `mutex` 所有权标志的值设为 `false`。

## <a name="swap"></a>  swap

将关联的 `mutex` 和所有权状态与指定对象的互换。

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>参数

`Other` A`unique_lock`对象。

## <a name="try_lock"></a>try_lock

在不阻止的情况下尝试获取关联 `mutex` 的所有权。

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>返回值

如果此方法成功获取 `true` 的所有权，则为 `mutex`；否则为 `false`。

### <a name="remarks"></a>备注

如果存储的 `mutex` 指针为 `null`，则此方法将引发一个错误代码为 `operation_not_permitted` 的 [system_error](../standard-library/system-error-class.md)。

如果调用线程已拥有 `mutex`，则此方法将引发一个错误代码为 `resource_deadlock_would_occur` 的 `system_error`。

## <a name="try_lock_for"></a>try_lock_for

在不阻止的情况下尝试获取关联 `mutex` 的所有权。

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>参数

`Rel_time` A [chrono:: duration](../standard-library/duration-class.md)对象，它指定的最大方法尝试获取的所有权的时间量`mutex`。

### <a name="return-value"></a>返回值

如果此方法成功获取 `true` 的所有权，则为 `mutex`；否则为 `false`。

### <a name="remarks"></a>备注

如果存储的 `mutex` 指针为 `null`，则此方法将引发一个错误代码为 `operation_not_permitted` 的 [system_error](../standard-library/system-error-class.md)。

如果调用线程已拥有 `mutex`，则此方法将引发一个错误代码为 `resource_deadlock_would_occur` 的 `system_error`。

## <a name="try_lock_until"></a>try_lock_until

在不阻止的情况下尝试获取关联 `mutex` 的所有权。

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>参数

`Abs_time` 一个指定之后此方法不再尝试获取的所有权的阈值的时间点在`mutex`。

### <a name="return-value"></a>返回值

如果此方法成功获取 `true` 的所有权，则为 `mutex`；否则为 `false`。

### <a name="remarks"></a>备注

如果存储的 `mutex` 指针为 `null`，则此方法将引发一个错误代码为 `operation_not_permitted` 的 [system_error](../standard-library/system-error-class.md)。

如果调用线程已拥有 `mutex`，则此方法将引发一个错误代码为 `resource_deadlock_would_occur` 的 `system_error`。

## <a name="unique_lock"></a>  unique_lock 构造函数

构造 `unique_lock` 对象。

```cpp
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```

### <a name="parameters"></a>参数

`Mtx` 一个互斥体类型对象。

`Rel_time` A [chrono:: duration](../standard-library/duration-class.md)对象，它指定的最大方法尝试获取的所有权的时间量`mutex`。

`Abs_time` 一个指定之后此方法不再尝试获取的所有权的阈值的时间点在`mutex`。

`Other` A`unique_lock`对象。

### <a name="remarks"></a>备注

第一个构造函数将构造一个对象，该对象包含值为 0 的关联 mutex 指针。

第二个构造函数将从 `Other` 中移动关联的 mutex 状态。 移动后，`Other` 将不再与 mutex 关联。

剩余构造函数将 & `Mtx` 存储为存储的 `mutex` 指针。 如果第二个参数存在，则由它确定 `mutex` 的所有权。

|||
|-|-|
|`No argument`|通过在关联的 `mutex` 对象上调用 `lock` 方法，获取所有权。|
|`Adopt`|已假定所有权。 调用构造函数时，必须锁定 `Mtx`。|
|`Defer`|假定调用线程不包含 `mutex` 对象。 调用构造函数时，不得锁定 `Mtx`。|
|`Try`|通过在关联的 `mutex` 对象上调用 `try_lock`，确定所有权。 此构造函数不会引发任何操作。|
|`Rel_time`|通过调用 `try_lock_for(Rel_time)` 确定所有权。|
|`Abs_time`|通过调用 `try_lock_until(Abs_time)` 确定所有权。|

## <a name="dtorunique_lock_destructor"></a>~unique_lock 析构函数

释放与 `unique_lock` 对象关联的所有资源。

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>备注

如果调用线程拥有关联的 `mutex`，则析构函数通过调用 `mutex` 对象上的 unlock 来释放所有权。

## <a name="unlock"></a>unlock

释放关联的 `mutex` 的所有权。

```cpp
void unlock();
```

### <a name="remarks"></a>备注

如果调用线程没有关联的 `mutex`，则此方法将引发一个错误代码为 `operation_not_permitted` 的 [system_error](../standard-library/system-error-class.md)。

否则，此方法将在关联的 `mutex` 上调用 `unlock`，并将内部线程所有权标志设为 `false`。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
