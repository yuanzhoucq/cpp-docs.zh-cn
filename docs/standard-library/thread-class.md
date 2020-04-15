---
title: thread 类
ms.date: 11/04/2016
f1_keywords:
- thread/std::thread
- thread/std::thread::id Class
- thread/std::thread::thread
- thread/std::thread::detach
- thread/std::thread::get_id
- thread/std::thread::hardware_concurrency
- thread/std::thread::join
- thread/std::thread::joinable
- thread/std::thread::native_handle
- thread/std::thread::swap
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
helpviewer_keywords:
- std::thread [C++]
- std::thread [C++], thread
- std::thread [C++], detach
- std::thread [C++], get_id
- std::thread [C++], hardware_concurrency
- std::thread [C++], join
- std::thread [C++], joinable
- std::thread [C++], native_handle
- std::thread [C++], swap
ms.openlocfilehash: 13996a8ec4ab56fc56a78606d1a2ce8d76994c0d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375857"
---
# <a name="thread-class"></a>thread 类

定义用于查看和管理应用程序中执行线程的对象。

## <a name="syntax"></a>语法

```cpp
class thread;
```

## <a name="remarks"></a>备注

可以使用**线程**对象观察和管理应用程序中的执行线程。 使用默认构造函数创建的线程对象不与任何执行线程相关联。 通过使用可调用对象构造的线程对象创建一个新的执行线程，并在该线程中调用可调用对象。 可移动线程对象，但不能复制。 因此，执行线程只与一个线程对象相关联。

每个执行线程都具有 `thread::id` 类型的唯一标识符。 函数 `this_thread::get_id` 返回调用线程的标识符。 成员函数`thread::get_id` 返回由线程对象管理的线程标识符。 对于默认构造的线程对象，`thread::get_id` 方法返回具有值的对象，该值与所有默认构造线程对象的值相同但和 `this_thread::get_id` 返回的任何线程（可在调用时连接）的值不同。

## <a name="members"></a>成员

### <a name="public-classes"></a>公共类

|名称|说明|
|----------|-----------------|
|[thread::id Class](#id_class)|标识唯一关联的线程。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[线程 (thread)](#thread)|构造**线程**对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[分离](#detach)|从**线程**对象分离关联的线程。|
|[get_id](#get_id)|返回关联线程的唯一标识符。|
|[hardware_concurrency](#hardware_concurrency)|静态。 返回硬件线程上下文的估计数量。|
|[加入](#join)|阻止，直到完成关联的线程。|
|[可联接](#joinable)|指定关联的线程是否可联接。|
|[native_handle](#native_handle)|返回表示线程句柄的特定于实现的类型。|
|[交换](#swap)|将对象状态与指定的**线程**对象交换。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[线程：：运算符*](#op_eq)|将线程与当前**线程**对象关联。|

## <a name="requirements"></a>要求

**标题：**\<线程>

**命名空间:** std

## <a name="threaddetach"></a><a name="detach"></a>线程：:d埃塔奇

拆离相关联的线程。 操作系统负责释放终止的线程资源。

```cpp
void detach();
```

### <a name="remarks"></a>备注

调用 `detach` 后，再调用 [get_id](#get_id)，返回[id](#id_class)。

如果与调用对象关联的线程不可联接，该函数将引发将引发一个错误代码为 `invalid_argument` 的 [system_error](../standard-library/system-error-class.md)。

如果与调用对象相关联的线程无效，该函数将引发将引发一个错误代码为 `no_such_process` 的 `system_error`。

## <a name="threadget_id"></a><a name="get_id"></a>线程：：get_id

返回关联线程的唯一标识符。

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>返回值

一个 [thread:: id](#id_class) 对象，唯一标识相关联的线程，如果该对象没有任何关联的线程，则为 `thread::id()`。

## <a name="threadhardware_concurrency"></a><a name="hardware_concurrency"></a>线程：：hardware_concurrency

静态方法，返回硬件线程上下文数量的估计值。

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>返回值

硬件线程上下文数量的估计值。 如果无法计算该值或该值未正确定义，此方法将返回 0。

## <a name="threadid-class"></a><a name="id_class"></a>线程：：id 类

为过程中的每个执行线程提供唯一标识符。

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>备注

默认构造函数创建一个对象，该对象与任何现有线程的 `thread::id` 对象都不相等。

所有默认构造的 `thread::id` 对象都相等。

## <a name="threadjoin"></a><a name="join"></a>线程：：联接

阻止，直到完成与调用对象相关联的执行线程。

```cpp
void join();
```

### <a name="remarks"></a>备注

调用成功后，再继续调用 [get_id](#get_id)，以便调用对象返回默认值 [thread:: id](#id_class)，该默认值与任何现有线程的 `thread::id` 都不相等；如果调用不成功，`get_id` 返回的值保持不变。

## <a name="threadjoinable"></a><a name="joinable"></a>线程：：可联接

指定关联的线程是否*可联接*。

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>返回值

如果关联的线程*是可联接的*，**则为 true** ;否则，**假**。

### <a name="remarks"></a>备注

如果 `get_id() != id()`，则线程对象可联接**。

## <a name="threadnative_handle"></a><a name="native_handle"></a>线程：：native_handle

返回表示线程句柄的特定于实现的类型。 可以以特定于实现的方式使用线程句柄。

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>返回值

`native_handle_type` 被定义为可强制转化为 `void *` 的 Win32 `HANDLE`。

## <a name="threadoperator"></a><a name="op_eq"></a>线程：：运算符*

将指定对象的线程与当前对象相关联。

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>参数

*其他*\
**线程**对象。

### <a name="return-value"></a>返回值

`*this`

### <a name="remarks"></a>备注

如果调用对象可联接，该方法会调用拆离。

建立关联后，将 `Other` 设置为默认构造状态。

## <a name="threadswap"></a><a name="swap"></a>线程：：交换

将对象状态与指定**线程**对象的状态交换。

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>参数

*其他*\
**线程**对象。

## <a name="threadthread-constructor"></a><a name="thread"></a>线程：线程构造函数

构造**线程**对象。

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>参数

*F*\
要由线程执行的应用程序所定义的函数。

*A*\
要传递给*F*的参数列表。

*其他*\
现有**线程**对象。

### <a name="remarks"></a>备注

第一个构造函数构造与执行线程不相关联的对象。 通过调用 `get_id` 返回的构造对象的值为 `thread::id()`。

第二个构造函数构造一个与新的执行线程关联的对象，并执行在`INVOKE`[\<函数>](../standard-library/functional.md)中定义的伪函数。 如果用于启动新线程的资源不足，该函数将引发一个错误代码为 `resource_unavailable_try_again` 的 [system_error](../standard-library/system-error-class.md) 对象。 如果对*F*的调用以未捕获的异常终止，则调用[终止](../standard-library/exception-functions.md#terminate)。

第三个构造函数将构造一个对象，该对象与关联 `Other` 的线程相关。 随后， `Other` 会被设置为默认构造状态。

## <a name="see-also"></a>另请参阅

[标题文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<线程>](../standard-library/thread.md)
