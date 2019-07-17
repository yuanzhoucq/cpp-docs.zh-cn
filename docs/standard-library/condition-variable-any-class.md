---
title: condition_variable_any 类
ms.date: 11/04/2016
f1_keywords:
- condition_variable/std::condition_variable_any
- condition_variable/std::condition_variable_any::condition_variable_any
- condition_variable/std::condition_variable_any::notify_all
- condition_variable/std::condition_variable_any::notify_one
- condition_variable/std::condition_variable_any::wait
- condition_variable/std::condition_variable_any::wait_for
- condition_variable/std::condition_variable_any::wait_until
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
helpviewer_keywords:
- std::condition_variable_any
- std::condition_variable_any::condition_variable_any
- std::condition_variable_any::notify_all
- std::condition_variable_any::notify_one
- std::condition_variable_any::wait
- std::condition_variable_any::wait_for
- std::condition_variable_any::wait_until
ms.openlocfilehash: 7ecf13974404ec6e223d5d3e7387a70526eeefcc
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244650"
---
# <a name="conditionvariableany-class"></a>condition_variable_any 类

使用类 `condition_variable_any` 来等待具有任何 `mutex` 类型的事件。

## <a name="syntax"></a>语法

```cpp
class condition_variable_any;
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[condition_variable_any](#condition_variable_any)|构造 `condition_variable_any` 对象。|

### <a name="functions"></a>函数

|||
|-|-|
|[notify_all](#notify_all)|取消阻止正在等待 `condition_variable_any` 对象的所有线程。|
|[notify_one](#notify_one)|取消阻止正在等待 `condition_variable_any` 对象的某个线程。|
|[等待](#wait)|阻止线程。|
|[wait_for](#wait_for)|阻止某个线程，并设置线程阻止的时间间隔。|
|[wait_until](#wait_until)|阻止某个线程，并设置线程阻止的最大时间点。|

## <a name="condition_variable_any"></a> condition_variable_any

构造 `condition_variable_any` 对象。

```cpp
condition_variable_any();
```

### <a name="remarks"></a>备注

如果没有足够的内存，构造函数将抛出包含 `not_enough_memory` 错误代码的 [system_error](../standard-library/system-error-class.md) 对象。 如果由于某些其他资源不可用导致无法构造该对象，则构造函数将抛出包含 `resource_unavailable_try_again` 错误代码的 `system_error` 对象。

## <a name="notify_all"></a> notify_all

取消阻止正在等待 `condition_variable_any` 对象的所有线程。

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a> notify_one

取消阻止正在 `condition_variable_any` 对象上等待的某个线程。

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a> 等待

阻止线程。

```cpp
template <class Lock>
void wait(Lock& Lck);

template <class Lock, class Predicate>
void wait(Lock& Lck, Predicate Pred);
```

### <a name="parameters"></a>参数

*一个 Lck*\
任何类型的 `mutex` 对象。

*Pred*\
任何返回的表达式 **，则返回 true**或**false**。

### <a name="remarks"></a>备注

第一种方法进行阻止，直到通过调用 [notify_one](../standard-library/condition-variable-class.md#notify_one) 或 [notify_all](../standard-library/condition-variable-class.md#notify_all) 对 `condition_variable_any` 对象发出信号。 它还可错误唤醒。

第二种方法实际上执行以下代码。

```cpp
while (!Pred())
    wait(Lck);
```

## <a name="wait_for"></a> wait_for

阻止某个线程，并设置线程阻止的时间间隔。

```cpp
template <class Lock, class Rep, class Period>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time);

template <class Lock, class Rep, class Period, class Predicate>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time, Predicate Pred);
```

### <a name="parameters"></a>参数

*一个 Lck*\
任何类型的 `mutex` 对象。

*Rel_time*\
`chrono::duration` 对象指定线程唤醒前的时间。

*Pred*\
任何返回的表达式 **，则返回 true**或**false**。

### <a name="return-value"></a>返回值

第一种方法返回`cv_status::timeout`如果时等待终止*Rel_time*已过。 否则，该方法将返回 `cv_status::no_timeout`。

第二种方法返回的值*Pred*。

### <a name="remarks"></a>备注

第一种方法进行阻止，直到`condition_variable_any`对象通过调用发出信号[notify_one](../standard-library/condition-variable-class.md#notify_one)或[notify_all](../standard-library/condition-variable-class.md#notify_all)，或直到时间间隔*Rel_time*已过。 它还可错误唤醒。

第二种方法实际上执行以下代码。

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a> wait_until

阻止某个线程，并设置线程阻止的最大时间点。

```cpp
template <class Lock, class Clock, class Duration>
void wait_until(Lock& Lck, const chrono::time_point<Clock, Duration>& Abs_time);

template <class Lock, class Clock, class Duration, class Predicate>
void wait_until(
    Lock& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

template <class Lock>
void wait_until(Lock Lck, const xtime* Abs_time);

template <class Lock, class Predicate>
void wait_until(
    Lock Lck,
    const xtime* Abs_time,
    Predicate Pred);
```

### <a name="parameters"></a>参数

*一个 Lck*\
Mutex 对象。

*Abs_time*\
[chrono::time_point](../standard-library/time-point-class.md) 对象。

*Pred*\
任何返回的表达式 **，则返回 true**或**false**。

### <a name="return-value"></a>返回值

返回的方法`cv_status`键入返回`cv_status::timeout`如果时等待终止*Abs_time*结束。 否则，方法返回 `cv_status::no_timeout`。

返回的方法`bool`返回的值*Pred*。

### <a name="remarks"></a>备注

第一种方法进行阻止，直到`condition_variable`对象通过调用发出信号[notify_one](../standard-library/condition-variable-class.md#notify_one)或[notify_all](../standard-library/condition-variable-class.md#notify_all)，或直到*Abs_time*。 它还可错误唤醒。

第二种方法实际上执行以下代码。

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

第三种和第四种方法使用指向 `xtime` 类型的对象的指针来替换 `chrono::time_point` 对象。 `xtime` 对象指定等待信号的最大时间。
