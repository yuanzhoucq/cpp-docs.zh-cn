---
title: promise 类
ms.date: 10/18/2018
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.openlocfilehash: a6541fefb2423853f8e59a662e1c8a37777dc14c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323044"
---
# <a name="promise-class"></a>promise 类

描述*异步提供程序*。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
class promise;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[承诺](#promise)|构造 `promise` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[get_future](#get_future)|返回与此 promise 关联的 [future](../standard-library/future-class.md)。|
|[set_exception](#set_exception)|以原子方式设置此 promise 的结果以指示异常。|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|以原子方式设置此 promise 的结果以指示异常，并且仅在销毁当前线程中的所有线程本地对象后（通常在线程退出时）发出通知。|
|[set_value](#set_value)|以原子方式设置此 promise 的结果以指示值。|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|以原子方式设置此 promise 的结果以指示值，并且仅在销毁当前线程中的所有线程本地对象后（通常在线程退出时）发出通知。|
|[交换](#swap)|用指定的 promise 对象的*关联的异步状态*交换此 promise 的关联的异步状态。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[承诺：：操作员*](#op_eq)|此 promise 对象的共享状态的分配。|

## <a name="inheritance-hierarchy"></a>继承层次结构

*承诺*

## <a name="requirements"></a>要求

**标题：**\<未来>

**命名空间:** std

## <a name="promiseget_future"></a><a name="get_future"></a>承诺：：get_future

返回具有与此 promise 相同的*关联异步状态*的 [future](../standard-library/future-class.md) 对象。

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>备注

如果 promise 对象为空，则此方法将引发一个 [error_code](../standard-library/error-code-class.md) 为 `no_state` 的 [future_error](../standard-library/future-error-class.md)。

如果此方法已调用具有相同关联异步状态的承诺对象，则此方法将引发 `future_error` 为 `error_code` 的 `future_already_retrieved`。

## <a name="promiseoperator"></a><a name="op_eq"></a>承诺：：操作员*

从指定`promise`对象传输*关联的异步状态*。

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>参数

*其他*\
`promise` 对象。

### <a name="return-value"></a>返回值

`*this`

### <a name="remarks"></a>备注

此运算符从*其他*传输关联的异步状态。 转移后，*其他*为*空*。

## <a name="promisepromise-constructor"></a><a name="promise"></a>承诺：:p罗马结构器

构造 `promise` 对象。

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>参数

*铝*\
内存分配器。 有关详细信息[\<，请参阅分配器>。](../standard-library/allocators-header.md)

*其他*\
`promise` 对象。

### <a name="remarks"></a>备注

第一个构造函数构造*一个空*`promise`对象。

第二个构造函数构造一个`promise`空对象，并使用*Al*进行内存分配。

第三个构造函数构造一`promise`个对象，并从*其他*传输关联的异步状态，并将*其他*为空。

## <a name="promiseset_exception"></a><a name="set_exception"></a>承诺：：set_exception

以原子方式将异常存储为此 `promise` 对象的结果，并将“关联的异步状态”** 设置为“就绪”**。

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>参数

*Exc*\
通过此方法另存为异常结果的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)。

### <a name="remarks"></a>备注

如果 `promise` 对象没有关联的异步状态，则此方法将引发具有错误代码 `no_state` 的 [future_error](../standard-library/future-error-class.md)。

如果已为具有相同的关联异步状态的 `promise` 对象调用 `set_exception`、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、[set_value](#set_value) 或 [set_value_at_thread_exit](#set_value_at_thread_exit)，则此方法将引发具有错误代码 `promise_already_satisfied` 的 `future_error`。

此方法的结果是，不再阻止在关联的异步状态上受阻的任何线程。

## <a name="promiseset_exception_at_thread_exit"></a><a name="set_exception_at_thread_exit"></a>承诺：：set_exception_at_thread_exit

以原子方式设置此 `promise` 的结果以指示异常，并且仅在当前线程中的所有线程本地对象被销毁后（通常在线程退出时）发出通知。

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>参数

*Exc*\
通过此方法另存为异常结果的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)。

### <a name="remarks"></a>备注

如果 promise 对象没有关联的异步状态**，则此方法将引发具有错误代码 `no_state` 的 [future_error](../standard-library/future-error-class.md)。

如果[已为](#set_exception)具有相同关联`set_exception_at_thread_exit`异步状态`promise`的对象set_exception [、set_value](#set_value)或[set_value_at_thread_exit，](#set_value_at_thread_exit)则此方法将引发具有 的错误代码 的`future_error``promise_already_satisfied`。

与 [set_exception](#set_exception) 相反，此方法在当前线程中的所有线程本地对象被销毁前不会将关联的异步状态设置为已就绪。 通常，在关联的异步状态上受阻的线程会受到阻止，直到当前线程退出。

## <a name="promiseset_value"></a><a name="set_value"></a>承诺：：set_value

以原子方式将值存储为此 `promise` 对象的结果，并将“关联的异步状态”** 设置为“就绪”**。

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>参数

*瓦尔*\
要存储为结果的值。

### <a name="remarks"></a>备注

如果 `promise` 对象没有关联的异步状态，则此方法将引发具有错误代码 `no_state` 的 [future_error](../standard-library/future-error-class.md)。

如果已为具有相同的关联异步状态的 `promise` 对象调用 [set_exception](#set_exception)、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、`set_value` 或 [set_value_at_thread_exit](#set_value_at_thread_exit)，则此方法将引发具有错误代码 `promise_already_satisfied` 的 `future_error`。

此方法的结果是，不再阻止在关联的异步状态上受阻的任何线程。

第一种方法还会引发将*Val*复制到关联的异步状态时引发的任何异常。 在此情况下，关联的异步状态不设置为“就绪”。

第二种方法还会引发在*将 Val*移动到关联的异步状态时引发的任何异常。 在此情况下，关联的异步状态不设置为“就绪”。

对于部分专业化化`promise<Ty&>`，存储的值实际上是对*Val*的引用。

对于专用化 `promise<void>`，不存在任何存储的值。

## <a name="promiseset_value_at_thread_exit"></a><a name="set_value_at_thread_exit"></a>承诺：：set_value_at_thread_exit

以原子方式将值存为此 `promise` 对象的结果。

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>参数

*瓦尔*\
要存储为结果的值。

### <a name="remarks"></a>备注

如果 promise 对象没有关联的异步状态**，则此方法将引发具有错误代码 `no_state` 的 [future_error](../standard-library/future-error-class.md)。

如果已为具有相同的关联异步状态的 `promise` 对象调用 [set_exception](#set_exception)、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、[set_value](#set_value) 或 `set_value_at_thread_exit`，则此方法将引发具有错误代码 `promise_already_satisfied` 的 `future_error`。

与 `set_value` 相反，在当前线程中的所有线程本地对象被销毁前不会将关联的异步状态设置为已就绪。 通常，在关联的异步状态上受阻的线程会受到阻止，直到当前线程退出。

第一种方法还会引发将*Val*复制到关联的异步状态时引发的任何异常。

第二种方法还会引发在*将 Val*移动到关联的异步状态时引发的任何异常。

对于部分专业化`promise<Ty&>`化，存储值实际上是对*Val*的引用。

对于专用化 `promise<void>`，不存在任何存储的值。

## <a name="promiseswap"></a><a name="swap"></a>承诺：：交换

将此 promise 对象的*关联异步状态*与指定对象的交换。

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>参数

*其他*\
`promise` 对象。

## <a name="see-also"></a>另请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
