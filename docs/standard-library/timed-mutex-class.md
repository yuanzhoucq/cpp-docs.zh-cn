---
title: timed_mutex 类
ms.date: 11/04/2016
f1_keywords:
- mutex/std::timed_mutex
- mutex/std::timed_mutex::timed_mutex
- mutex/std::timed_mutex::lock
- mutex/std::timed_mutex::try_lock
- mutex/std::timed_mutex::try_lock_for
- mutex/std::timed_mutex::try_lock_until
- mutex/std::timed_mutex::unlock
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
helpviewer_keywords:
- std::timed_mutex [C++]
- std::timed_mutex [C++], timed_mutex
- std::timed_mutex [C++], lock
- std::timed_mutex [C++], try_lock
- std::timed_mutex [C++], try_lock_for
- std::timed_mutex [C++], try_lock_until
- std::timed_mutex [C++], unlock
ms.openlocfilehash: 6b9785dc41791be63d585d18802953eade370b2a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459923"
---
# <a name="timedmutex-class"></a>timed_mutex 类

表示定时互斥体类型。 此类型的对象在程序内通过时间限制阻止强制实现互相排斥。

## <a name="syntax"></a>语法

```cpp
class timed_mutex;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|构造未锁定的 `timed_mutex` 对象。|
|[timed_mutex::~timed_mutex 构造函数](#dtortimed_mutex_destructor)|释放由 `timed_mutex` 对象使用的任何资源。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[lock](#lock)|阻止调用线程，直到线程获取 `mutex` 的所有权。|
|[try_lock](#try_lock)|在不阻止的情况下尝试获取 `mutex` 的所有权。|
|[try_lock_for](#try_lock_for)|尝试获取在指定时间间隔内有效的 `mutex` 的所有权。|
|[try_lock_until](#try_lock_until)|尝试获取在指定时间之前有效的 `mutex` 的所有权。|
|[unlock](#unlock)|释放 `mutex` 的所有权。|

## <a name="requirements"></a>要求

**标头:** \<mutex >

**命名空间：** std

## <a name="lock"></a>  timed_mutex::lock

阻止调用线程，直到线程获取 `mutex` 的所有权。

```cpp
void lock();
```

### <a name="remarks"></a>备注

如果调用线程已拥有 `mutex`，则该行为不确定。

## <a name="timed_mutex"></a>timed_mutex::timed_mutex 构造函数

构造未锁定的 `timed_mutex` 对象。

```cpp
timed_mutex();
```

## <a name="dtortimed_mutex_destructor"></a>timed_mutex::~timed_mutex 析构函数

释放由 `mutex` 对象使用的任何资源。

```cpp
~timed_mutex();
```

### <a name="remarks"></a>备注

如果当析构函数运行时对象被锁定，则该行为不确定。

## <a name="try_lock"></a>  timed_mutex::try_lock

在不阻止的情况下尝试获取 `mutex` 的所有权。

```cpp
bool try_lock();
```

### <a name="return-value"></a>返回值

如果方法成功获取的`mutex`所有权, 则**为 true** ; 否则为**false**。

### <a name="remarks"></a>备注

如果调用线程已拥有 `mutex`，则该行为不确定。

## <a name="try_lock_for"></a>  timed_mutex::try_lock_for

在不阻止的情况下尝试获取 `mutex` 的所有权。

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>参数

*Rel_time*\
一个 [chrono::duration](../standard-library/duration-class.md) 对象，指定此方法尝试获取 `mutex` 所有权的最大时间量。

### <a name="return-value"></a>返回值

如果方法成功获取的`mutex`所有权, 则**为 true** ; 否则为**false**。

### <a name="remarks"></a>备注

如果调用线程已拥有 `mutex`，则该行为不确定。

## <a name="try_lock_until"></a>  timed_mutex::try_lock_until

在不阻止的情况下尝试获取 `mutex` 的所有权。

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>参数

*Abs_time*\
一个时间点，指定阈值，在此之后此方法不再尝试获取 `mutex` 所有权。

### <a name="return-value"></a>返回值

如果方法成功获取的`mutex`所有权, 则**为 true** ; 否则为**false**。

### <a name="remarks"></a>备注

如果调用线程已拥有 `mutex`，则该行为不确定。

## <a name="unlock"></a>timed_mutex:: unlock

释放 `mutex` 的所有权。

```cpp
void unlock();
```

### <a name="remarks"></a>备注

如果调用的线程不拥有 `mutex`，则该行为不确定。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
