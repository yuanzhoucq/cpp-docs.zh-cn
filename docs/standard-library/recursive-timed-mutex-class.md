---
title: recursive_timed_mutex 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::lock
- mutex/std::recursive_timed_mutex::try_lock
- mutex/std::recursive_timed_mutex::try_lock_for
- mutex/std::recursive_timed_mutex::try_lock_until
- mutex/std::recursive_timed_mutex::unlock
dev_langs:
- C++
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::recursive_timed_mutex [C++]
- std::recursive_timed_mutex [C++], recursive_timed_mutex
- std::recursive_timed_mutex [C++], lock
- std::recursive_timed_mutex [C++], try_lock
- std::recursive_timed_mutex [C++], try_lock_for
- std::recursive_timed_mutex [C++], try_lock_until
- std::recursive_timed_mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: f30cf00a1e551c8d25b17d3a876d556ecea40c9e
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107635"
---
# <a name="recursivetimedmutex-class"></a>recursive_timed_mutex 类

表示定时互斥体类型。 此类型的对象用于在程序内通过使用时间限制阻止来强制实现互相排斥。 与 [timed_mutex](../standard-library/timed-mutex-class.md) 类型的对象不同，为 `recursive_timed_mutex` 对象调用锁定方法的效果是有明确定义的。

## <a name="syntax"></a>语法

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|构造未锁定的 `recursive_timed_mutex` 对象。|
|[~recursive_timed_mutex 析构函数](#dtorrecursive_timed_mutex_destructor)|释放由 `recursive_timed_mutex` 对象使用的任何资源。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[lock](#lock)|阻止调用线程，直到线程获取 `mutex` 的所有权。|
|[try_lock](#try_lock)|在不阻止的情况下尝试获取 `mutex` 的所有权。|
|[try_lock_for](#try_lock_for)|尝试获取在指定时间间隔内有效的 `mutex` 的所有权。|
|[try_lock_until](#try_lock_until)|尝试获取在指定时间之前有效的 `mutex` 的所有权。|
|[unlock](#unlock)|释放 `mutex` 的所有权。|

## <a name="requirements"></a>要求

**标头：** \<互斥体 >

**命名空间：** std

## <a name="lock"></a>lock

阻止调用线程，直到线程获取 `mutex` 的所有权。

```cpp
void lock();
```

### <a name="remarks"></a>备注

如果调用线程已拥有 `mutex`，则该方法将立即返回，同时上一锁定保持有效。

## <a name="recursive_timed_mutex"></a>  recursive_timed_mutex 构造函数

构造未锁定的 `recursive_timed_mutex` 对象。

```cpp
recursive_timed_mutex();
```

## <a name="dtorrecursive_timed_mutex_destructor"></a>  ~recursive_timed_mutex 析构函数

释放由 `recursive_timed_mutex` 对象使用的任何资源。

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>备注

如果当析构函数运行时对象被锁定，则该行为不确定。

## <a name="try_lock"></a>try_lock

在不阻止的情况下尝试获取 `mutex` 的所有权。

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>返回值

**true**如果此方法成功获取的所有权`mutex`或如果调用线程已拥有`mutex`; 否则为**false**。

### <a name="remarks"></a>备注

如果调用线程已拥有`mutex`，该函数将立即返回**true**，和上一锁定保持有效。

## <a name="try_lock_for"></a>try_lock_for

在不阻止的情况下尝试获取 `mutex` 的所有权。

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>参数

*Rel_time*<br/>
一个 [chrono::duration](../standard-library/duration-class.md) 对象，指定此方法尝试获取 `mutex` 所有权的最大时间量。

### <a name="return-value"></a>返回值

**true**如果此方法成功获取的所有权`mutex`或如果调用线程已拥有`mutex`; 否则为**false**。

### <a name="remarks"></a>备注

如果调用线程已拥有`mutex`，该方法立即返回**true**，和上一锁定保持有效。

## <a name="try_lock_until"></a>try_lock_until

在不阻止的情况下尝试获取 `mutex` 的所有权。

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>参数

*Abs_time*<br/>
一个时间点，指定阈值，在此之后此方法不再尝试获取 `mutex` 所有权。

### <a name="return-value"></a>返回值

**true**如果此方法成功获取的所有权`mutex`或如果调用线程已拥有`mutex`; 否则为**false**。

### <a name="remarks"></a>备注

如果调用线程已拥有`mutex`，该方法立即返回**true**，和上一锁定保持有效。

## <a name="unlock"></a>unlock

释放 `mutex` 的所有权。

```cpp
void unlock();
```

### <a name="remarks"></a>备注

仅当 `mutex` 的调用次数与在 `recursive_timed_mutex` 对象上成功调用 [lock](#lock)、[try_lock](#try_lock)、[try_lock_for](#try_lock_for) [try_lock_until](#try_lock_until) 的次数一样多时，此方法才释放其所有权。

如果调用的线程不拥有 `mutex`，则该行为不确定。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
