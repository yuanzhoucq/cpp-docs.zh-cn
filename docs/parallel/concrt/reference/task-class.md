---
title: task 类（并发运行时）
ms.date: 07/30/2019
f1_keywords:
- task
- PPLTASKS/concurrency::task
- PPLTASKS/concurrency::task::task
- PPLTASKS/concurrency::task::get
- PPLTASKS/concurrency::task::is_apartment_aware
- PPLTASKS/concurrency::task::is_done
- PPLTASKS/concurrency::task::scheduler
- PPLTASKS/concurrency::task::then
- PPLTASKS/concurrency::task::wait
helpviewer_keywords:
- task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
ms.openlocfilehash: 6a063f0bba9482824817e4efe21ae5b7bf3c0995
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219529"
---
# <a name="task-class-concurrency-runtime"></a>task 类（并发运行时）

并行模式库 (PPL) `task` 类。 `task`对象表示可与其他任务同时异步执行的工作，以及并发运行时中并行算法生成的并行工作。 成功完成后，它将生成类型为 `_ResultType` 的结果。 类型为 `task<void>` 的任务不生成任何结果。 可独立于其他任务等待和取消的任务。 它还可以与使用延续（ `then` ）和 join （） `when_all` 和 choice （）模式的其他任务组合在一起 `when_any` 。 当任务对象被分配给新变量时，行为是的 `std::shared_ptr` ; 换言之，这两个对象表示相同的基础任务。

## <a name="syntax"></a>语法

```cpp
template <>
class task<void>;

template<typename _ResultType>
class task;
```

### <a name="parameters"></a>参数

*_ResultType*<br/>
任务生成的结果的类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`result_type`|此类的一个对象生成的结果类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[任务](#ctor)|已重载。 构造 `task` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[get](#get)|已重载。 返回此任务产生的结果。 如果任务不处于终止状态，则对 `get` 的调用将等待任务完成。 当使用的为的任务调用时，此方法不返回值 `result_type` **`void`** 。|
|[is_apartment_aware](#is_apartment_aware)|确定任务是否解包 Windows 运行时 `IAsyncInfo` 接口或继承自此类任务。|
|[is_done](#is_done)|确定任务是否已完成。|
|[日程](#scheduler)|返回此任务的计划程序|
|[接着](#then)|已重载。 向此任务添加延续任务。|
|[再](#wait)|等待此任务到达终止状态。 `wait` 可执行内联任务，前提是所有任务依赖项得到满足并且后台辅助线程没有选取它执行。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator！ =](#operator_neq)|已重载。 确定两个 `task` 对象是否表示不同的内部任务。|
|[operator =](#operator_eq)|已重载。 将一个 `task` 对象的内容替换为另一个对象的内容。|
|[operator = =](#operator_eq_eq)|已重载。 确定两个 `task` 对象是否表示相同的内部任务。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`task`

## <a name="requirements"></a>要求

**标头：** ppltasks。h

**命名空间：** 并发

## <a name="get"></a><a name="get"></a>获取

返回此任务产生的结果。 如果任务不处于终止状态，则对 `get` 的调用将等待任务完成。 当使用的为的任务调用时，此方法不返回值 `result_type` **`void`** 。

```cpp
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>返回值

任务的结果。

### <a name="remarks"></a>备注

如果任务已取消，则对的调用 `get` 将引发[task_canceled](task-canceled-class.md)异常。 如果任务遇到了不同的异常或异常从前面的任务传播到此任务，则对 `get` 的调用将引发该异常。

> [!IMPORTANT]
> 在通用 Windows 平台（UWP）应用程序中，不要[concurrency::task::wait](#wait) `get` `wait` `get` 在用户界面线程上运行的代码中调用 concurrency：： task：： wait 或（调用）。 否则，运行时会引发[concurrency：： invalid_operation](invalid-operation-class.md) ，因为这些方法会阻止当前线程，并可能导致应用程序停止响应。 但是，您可以调用 `get` 方法来接收基于任务的延续中的先行任务的结果，因为结果会立即可用。

## <a name="is_apartment_aware"></a><a name="is_apartment_aware"></a>is_apartment_aware

确定任务是否解包 Windows 运行时 `IAsyncInfo` 接口或继承自此类任务。

```cpp
bool is_apartment_aware() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果该任务对某个 `IAsyncInfo` 接口进行了解包或源自此类任务，则为 **`false`** ; 否则为。

## <a name="taskis_done-method-concurrency-runtime"></a><a name="is_done"></a>task：： is_done 方法（并发运行时）

确定任务是否已完成。

```cpp
bool is_done() const;
```

### <a name="return-value"></a>返回值

如果任务已完成，则为 True; 否则为 false。

### <a name="remarks"></a>备注

如果该任务已完成或已取消（有或没有用户例外），该函数将返回 true。

## <a name="operator"></a><a name="operator_neq"></a>operator！ =

确定两个 `task` 对象是否表示不同的内部任务。

```cpp
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要比较的任务。

### <a name="return-value"></a>返回值

**`true`** 如果对象引用不同的基础任务，则为 **`false`** ; 否则为。

## <a name="operator"></a><a name="operator_eq"></a>operator =

将一个 `task` 对象的内容替换为另一个对象的内容。

```cpp
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>参数

*_Other*<br/>
源 `task` 对象。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

`task` 的行为方式与智能指针的类似，在分配副本之后，此 `task` 对象与 `_Other` 表示相同的实际任务。

## <a name="operator"></a><a name="operator_eq_eq"></a>operator = =

确定两个 `task` 对象是否表示相同的内部任务。

```cpp
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要比较的任务。

### <a name="return-value"></a>返回值

**`true`** 如果对象引用相同的基础任务，则为 **`false`** ; 否则为。

## <a name="taskscheduler-method-concurrency-runtime"></a><a name="scheduler"></a>task：：计划程序方法（并发运行时）

返回此任务的计划程序

```cpp
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>返回值

指向计划程序的指针

## <a name="task"></a><a name="ctor"></a> 任务

构造 `task` 对象。

```cpp
task();

template<typename T>
__declspec(
    noinline) explicit task(T _Param);

template<typename T>
__declspec(
    noinline) explicit task(T _Param, const task_options& _TaskOptions);

task(
    const task& _Other);

task(
    task&& _Other);
```

### <a name="parameters"></a>参数

*T*<br/>
从中构造任务的参数的类型。

*_Param*<br/>
从中构造任务的参数。 如果在 Windows 运行时应用中使用任务，则这可能是 lambda、函数对象、 `task_completion_event<result_type>` 对象或 Windows：： Foundation：： IAsyncInfo。 Lambda 或函数对象应为等效于的类型 `std::function<X(void)>` ，其中 X 可以是类型为的变量， `result_type` `task<result_type>` 或在 Windows 运行时应用中为 Windows：： Foundation：： IAsyncInfo。

*_TaskOptions*<br/>
任务选项包括取消标记、计划程序等

*_Other*<br/>
源 `task` 对象。

### <a name="remarks"></a>备注

`task` 的默认构造函数仅用于允许在容器中使用任务。 只有在分配有效任务后才能使用默认的构造任务。 `get` `wait` `then` 在默认构造的任务上调用时，等方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

通过 `task_completion_event` 创建的任务将在设置任务完成事件后完成（并安排好其延续）。

采用取消标记的构造函数的版本可创建能够通过使用提供标记的 `cancellation_token_source` 取消的任务。 创建时没有使用取消标记的任务不可取消。

通过 `Windows::Foundation::IAsyncInfo` 接口或返回 `IAsyncInfo` 接口的 lambda 创建的任务在封闭的 Windows 运行时异步操作或行为完成时达到其终止状态。 同样，从返回的 lambda 中创建的任务 `task<result_type>` 在内部任务达到其终止状态时达到其终止状态，而不是在 lambda 返回时。

`task` 行为与智能指针的行为类似，可按值安全传递。 它可以由多个线程访问，而无需锁定。

采用 Windows：： Foundation：： IAsyncInfo 接口或返回此类接口的 lambda 的构造函数重载仅适用于 Windows 运行时应用。

有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="then"></a><a name="then"></a>接着

向此任务添加延续任务。

```cpp
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions = task_options()) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;
```

### <a name="parameters"></a>参数

*_Function*<br/>
此任务将调用的函数对象的类型。

*_Func*<br/>
此任务完成时要执行的延续函数。 此延续函数必须将 `result_type` 或 `task<result_type>` 的变量作为输入，其中 `result_type` 是此任务产生的结果的类型。

*_TaskOptions*<br/>
任务选项包括取消标记、计划程序和延续上下文。 默认情况下，前面的 3 个选项是从前面的任务继承的

*_CancellationToken*<br/>
要与延续任务相关联的取消标记。 创建时不带取消标记的延续任务将继承其前面的任务的标记。

*_ContinuationContext*<br/>
用于指定执行延续的位置的变量。 此变量仅在 UWP 应用中使用时才有用。 有关详细信息，请参阅[task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>返回值

新创建的延续任务。 返回任务的结果类型取决于 `_Func` 返回的内容。

### <a name="remarks"></a>备注

`then`采用返回 Windows：： Foundation：： IAsyncInfo 接口的 lambda 或函子的的重载仅适用于 Windows 运行时应用。

有关如何使用任务延续来编写异步工作的详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="wait"></a><a name="wait"></a>再

等待此任务到达终止状态。 `wait` 可执行内联任务，前提是所有任务依赖项得到满足并且后台辅助线程没有选取它执行。

```cpp
task_status wait() const;
```

### <a name="return-value"></a>返回值

可为 `task_status` 或 `completed` 的 `canceled` 值。 如果任务在执行期间遇到了异常或异常从前面的任务传播到此任务，则 `wait` 将引发该异常。

### <a name="remarks"></a>备注

> [!IMPORTANT]
> 在通用 Windows 平台（UWP）应用程序中，不要 `wait` 在用户界面线程上运行的代码中调用。 否则，运行时会引发 [concurrency::invalid_operation](invalid-operation-class.md) ，原因是此方法阻止当前线程并可能导致应用停止响应。 但是，你可以调用 [concurrency::task::get](#get) 方法来接收基于任务的延续中的先行任务的结果。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
