---
title: packaged_task 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- future/std::packaged_task
- future/std::packaged_task::packaged_task
- future/std::packaged_task::get_future
- future/std::packaged_task::make_ready_at_thread_exit
- future/std::packaged_task::reset
- future/std::packaged_task::swap
- future/std::packaged_task::valid
- future/std::packaged_task::operator()
- future/std::packaged_task::operator bool
dev_langs:
- C++
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::packaged_task [C++]
- std::packaged_task [C++], packaged_task
- std::packaged_task [C++], get_future
- std::packaged_task [C++], make_ready_at_thread_exit
- std::packaged_task [C++], reset
- std::packaged_task [C++], swap
- std::packaged_task [C++], valid
ms.workload:
- cplusplus
ms.openlocfilehash: b37d6fc7b01c179f017e04f8064a789b8f4ad2b9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860900"
---
# <a name="packagedtask-class"></a>packaged_task 类

描述异步提供程序，它是调用签名为 `Ty(ArgTypes...)` 的调用包装器。 除可能的结果外，其关联异步状态还保留可调用对象的副本。

## <a name="syntax"></a>语法

```cpp
template <class>
class packaged_task;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[packaged_task](#packaged_task)|构造 `packaged_task` 对象。|
|[packaged_task::~packaged_task 析构函数](#dtorpackaged_task_destructor)|销毁 `packaged_task` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[get_future](#get_future)|返回具有相同关联异步状态的 [future](../standard-library/future-class.md) 对象。|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|调用存储在关联异步状态中的可调用的对象，并以原子方式存储返回值。|
|[reset](#reset)|替换关联异步状态。|
|[swap](#swap)|将关联异步状态与指定对象的状态交换。|
|[valid](#valid)|指定对象是否具有关联异步状态。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[packaged_task::operator=](#op_eq)|从指定对象传输关联异步状态。|
|[packaged_task::operator()](#op_call)|调用存储在关联异步状态中的可调用的对象，以原子方式存储返回值，并将其状态设置为就绪。|
|[packaged_task::operator bool](#op_bool)|指定对象是否具有关联异步状态。|

## <a name="requirements"></a>要求

**标头：** \<将来 >

**命名空间：** std

## <a name="get_future"></a>packaged_task::get_future

返回具有相同关联异步状态的 `future<Ty>` 类型的对象。

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>备注

如果 `packaged_task` 对象没有关联的异步状态，则此方法将引发具有错误代码 `no_state` 的 [future_error](../standard-library/future-error-class.md)。

如果已为具有相同关联异步状态的 `packaged_task` 对象调用此方法，则此方法将引发具有错误代码 `future_already_retrieved` 的 `future_error`。

## <a name="make_ready_at_thread_exit"></a>packaged_task::make_ready_at_thread_exit

调用存储在关联异步状态中的可调用的对象，并以原子方式存储返回值。

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>备注

如果 `packaged_task` 对象没有关联的异步状态，则此方法将引发具有错误代码 `no_state` 的 [future_error](../standard-library/future-error-class.md)。

如果已为具有相同的关联异步状态的 `packaged_task` 对象调用此方法或 [make_ready_at_thread_exit](#make_ready_at_thread_exit)，则此方法将引发具有错误代码 `promise_already_satisfied` 的 `future_error`。

否则，此运算符会调用 `INVOKE(fn, args..., Ty)`，其中 *fn* 是存储在关联异步状态中的可调用的对象。 将任何返回值作为关联异步状态的返回结果以原子方式存储。

与 [packaged_task::operator()](#op_call) 相反，在正在调用的线程中的所有线程本地对象被销毁前不会将关联的异步状态设置为 `ready`。 通常，在关联的异步状态上受阻的线程会受到阻止，直到正在调用的线程退出。

## <a name="op_eq"></a>packaged_task::operator=

从指定的对象传输关联异步状态。

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>参数

`Right` A`packaged_task`对象。

### <a name="return-value"></a>返回值

`*this`

### <a name="remarks"></a>备注

操作后，`Right` 不再具有关联异步状态。

## <a name="op_call"></a>packaged_task::operator()

调用存储在关联异步状态中的可调用的对象，以原子方式存储返回值，并将其状态设置为就绪。

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>备注

如果 `packaged_task` 对象没有关联的异步状态，则此方法将引发具有错误代码 `no_state` 的 [future_error](../standard-library/future-error-class.md)。

如果已为具有相同的关联异步状态的 `packaged_task` 对象调用此方法或 [make_ready_at_thread_exit](#make_ready_at_thread_exit)，则此方法将引发具有错误代码 `promise_already_satisfied` 的 `future_error`。

否则，此运算符会调用 `INVOKE(fn, args..., Ty)`，其中 *fn* 是存储在关联异步状态中的可调用的对象。 将任何返回值作为关联异步状态的返回结果以原子方式存储，且状态设置为就绪。 结果，不再阻止在关联的异步状态上受阻的任何线程。

## <a name="op_bool"></a>packaged_task::operator bool

指定对象是否具有 `associated asynchronous state`。

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>返回值

如果对象有关联的异步状态，则为 `true`；否则为 `false`。

## <a name="packaged_task"></a>  packaged_task::packaged_task 构造函数

构造 `packaged_task` 对象。

```cpp
packaged_task() noexcept;
packaged_task(packaged_task&& Right) noexcept;
template <class Fn>
   explicit packaged_task(Fn&& fn);

template <class Fn, class Alloc>
   explicit packaged_task(
      allocator_arg_t, const Alloc& alloc, Fn&& fn);
```

### <a name="parameters"></a>参数

`Right` A`packaged_task`对象。

`alloc` 内存分配器。 有关详细信息，请参阅 [\<allocators>](../standard-library/allocators-header.md)。

`fn` 一个函数对象。

### <a name="remarks"></a>备注

第一个构造函数构造没有关联异步状态的 `packaged_task` 对象。

第二个构造函数构造 `packaged_task` 对象并从 `Right` 传输关联异步状态。 操作后，`Right` 不再具有关联异步状态。

第三个构造函数构造 `packaged_task` 对象，该对象具有存储在其关联异步状态中的 `fn` 的副本。

第四个构造函数构造 `packaged_task` 对象（该对象具有存储在其关联异步状态中的 `fn` 的副本）并使用 `alloc` 分配内存。

## <a name="dtorpackaged_task_destructor"></a>  packaged_task::~packaged_task 析构函数

销毁 `packaged_task` 对象。

```cpp
~packaged_task();
```

### <a name="remarks"></a>备注

如果关联异步状态未就绪，则析构函数将存储具有错误代码 `broken_promise` 的 [future_error](../standard-library/future-error-class.md) 异常作为关联异步状态中的结果，并且不再阻止在关联异步状态上受阻的任何线程。

## <a name="reset"></a>packaged_task::reset

使用新的关联异步状态替换现有的关联异步状态。

```cpp
void reset();
```

### <a name="remarks"></a>备注

实际上，此方法将执行 `*this = packaged_task(move(fn))`，其中 *fn* 是存储在此对象的关联异步状态中的函数对象。 因此，将清除该对象的状态，且可像在新构造的对象上一样调用 [get_future](#get_future)、[operator()](#op_call) 和 [make_ready_at_thread_exit](#make_ready_at_thread_exit)。

## <a name="swap"></a>  packaged_task::swap

将关联异步状态与指定对象的状态交换。

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>参数

`Right` A`packaged_task`对象。

## <a name="valid"></a>  packaged_task::valid

指定对象是否具有 `associated asynchronous state`。

```cpp
bool valid() const;
```

### <a name="return-value"></a>返回值

如果对象有关联的异步状态，则为 `true`；否则为 `false`。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
