---
title: '&lt;thread&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: 130328ca07de28e14eedd7fdc99fb8946f26c5cb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232854"
---
# <a name="ltthreadgt-functions"></a>&lt;thread&gt; 函数

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|
|[swap](#swap)|[yield](#yield)|

## <a name="get_id"></a><a name="get_id"></a>get_id

唯一标识当前的执行线程。

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>返回值

类型为 [thread:: id](../standard-library/thread-class.md) 的对象，用于唯一标识当前的执行线程。

## <a name="sleep_for"></a><a name="sleep_for"></a>sleep_for

阻止调用线程。

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>参数

*Rel_time*\
用于指定时间间隔的 [duration](../standard-library/duration-class.md) 对象。

### <a name="remarks"></a>备注

函数会阻止调用线程，至少*Rel_time*指定的时间。 此函数不引发任何异常。

## <a name="sleep_until"></a><a name="sleep_until"></a>sleep_until

阻止调用线程，至少直到指定的时间。

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>参数

*Abs_time*\
表示时间点。

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="swap"></a><a name="swap"></a>购

交换两个 `thread` 对象的状态。

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>参数

*左中*\
左 `thread` 对象。

*然后*\
正确的 `thread` 对象。

### <a name="remarks"></a>备注

函数调用 `Left.swap(Right)`。

## <a name="yield"></a><a name="yield"></a>产生

表示要运行其他线程的操作系统，即使当前线程会照常继续运行。

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>另请参阅

[\<thread>](../standard-library/thread.md)
