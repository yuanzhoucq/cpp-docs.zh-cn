---
title: task 类（并发运行时）
ms.date: 11/04/2016
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
ms.openlocfilehash: 99676ac0fff9584cd8453562f8918f6cadd66666
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278525"
---
# <a name="task-class-concurrency-runtime"></a>task 类（并发运行时）

并行模式库 (PPL) `task` 类。 `task` 对象，表示可异步执行的工作，以及可与并发运行时中的并行算法生成的其他任务一起执行的工作。 成功完成后，它将生成类型为 `_ResultType` 的结果。 类型为 `task<void>` 的任务不生成任何结果。 可独立于其他任务等待和取消的任务。 它还可以编写与其他任务使用继续符 ( `then`)，和联接 ( `when_all`) 和选择 ( `when_any`) 模式。

## <a name="syntax"></a>语法

```
template <typename T>
class task;

template <>
class task<void>;

template<typename _ReturnType>
class task;
```

#### <a name="parameters"></a>参数

*T*<br/>
任务对象类型。

*_ReturnType*<br/>
此任务的结果类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`result_type`|此类的一个对象生成的结果类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[task](#ctor)|已重载。 构造 `task` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[get](#get)|已重载。 返回此任务产生的结果。 如果任务不处于终止状态，则对 `get` 的调用将等待任务完成。 在调用 `result_type` 为 `void` 的任务时，此方法不返回值。|
|[is_apartment_aware](#is_apartment_aware)|确定任务是否解包 Windows 运行时 `IAsyncInfo` 接口或继承自此类任务。|
|[is_done](#is_done)|确定任务是否已完成。|
|[scheduler](#scheduler)|返回此任务的计划程序|
|[then](#then)|已重载。 向此任务添加延续任务。|
|[wait](#wait)|等待此任务到达终止状态。 `wait` 可执行内联任务，前提是所有任务依赖项得到满足并且后台辅助线程没有选取它执行。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator!=](#operator_neq)|已重载。 确定两个 `task` 对象是否表示不同的内部任务。|
|[operator=](#operator_eq)|已重载。 将一个 `task` 对象的内容替换为另一个对象的内容。|
|[operator==](#operator_eq_eq)|已重载。 确定两个 `task` 对象是否表示相同的内部任务。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`task`

## <a name="requirements"></a>要求

**标头：** ppltasks.h

**命名空间：** 并发

##  <a name="get"></a> 获取

返回此任务产生的结果。 如果任务不处于终止状态，则对 `get` 的调用将等待任务完成。 在调用 `result_type` 为 `void` 的任务时，此方法不返回值。

```
_ReturnType get() const;

void get() const;
```

### <a name="return-value"></a>返回值

任务的结果。

### <a name="remarks"></a>备注

如果任务已取消，调用`get`将引发[task_canceled](task-canceled-class.md)异常。 如果任务遇到了不同的异常或异常从前面的任务传播到此任务，则对 `get` 的调用将引发该异常。

> [!IMPORTANT]
>  在通用 Windows 平台 (UWP) 应用中，不要调用[concurrency::task::wait](#wait)或`get`(`wait`调用`get`) 中的用户界面线程运行的代码。 否则，运行时会引发[concurrency:: invalid_operation](invalid-operation-class.md)因为这些方法阻止当前线程，并可能导致应用停止响应。 但是，可以调用`get`方法来接收中基于任务的延续的先行任务的结果，因为结果立即可用。

##  <a name="is_apartment_aware"></a> is_apartment_aware

确定任务是否解包 Windows 运行时 `IAsyncInfo` 接口或继承自此类任务。

```
bool is_apartment_aware() const;
```

### <a name="return-value"></a>返回值

**true**如果任务解包`IAsyncInfo`接口或继承自此类任务**false**否则为。

##  <a name="is_done"></a>  task:: is_done 方法 （并发运行时）

确定任务是否已完成。

```
bool is_done() const;
```

### <a name="return-value"></a>返回值

如果任务已完成，false 否则，则为 true。

### <a name="remarks"></a>备注

如果任务已完成或取消 （有或没有用户异常），则函数返回 true。

##  <a name="operator_neq"></a> 运算符 ！ =

确定两个 `task` 对象是否表示不同的内部任务。

```
bool operator!= (const task<_ReturnType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要比较的任务。

### <a name="return-value"></a>返回值

**true**如果两个对象引用不同基础任务，并**false**否则为。

##  <a name="operator_eq"></a> 运算符 =

将一个 `task` 对象的内容替换为另一个对象的内容。

```
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>参数

*_Other*<br/>
源 `task` 对象。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

`task` 的行为方式与智能指针的类似，在分配副本之后，此 `task` 对象与 `_Other` 表示相同的实际任务。

##  <a name="operator_eq_eq"></a> 运算符 = =

确定两个 `task` 对象是否表示相同的内部任务。

```
bool operator== (const task<_ReturnType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
要比较的任务。

### <a name="return-value"></a>返回值

**true**如果对象引用同一基础任务，并**false**否则为。

##  <a name="scheduler"></a>  task:: scheduler 方法 （并发运行时）

返回此任务的计划程序

```
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>返回值

指向计划程序

##  <a name="ctor"></a> 任务

构造 `task` 对象。

```
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
从中构造任务的参数。 这可能是 lambda、 函数对象，`task_completion_event<result_type>`对象或 Windows::Foundation::IAsyncInfo 如果任务使用 Windows 运行时应用程序中。 Lambda 或函数对象应为类型等效于`std::function<X(void)>`，其中 X 可以是类型的变量`result_type`， `task<result_type>`，或在 Windows 运行时应用 Windows::Foundation::IAsyncInfo。

*_TaskOptions*<br/>
任务选项包括取消标记、计划程序等

*_Other*<br/>
源 `task` 对象。

### <a name="remarks"></a>备注

`task` 的默认构造函数仅用于允许在容器中使用任务。 只有在分配有效任务后才能使用默认的构造任务。 等方法`get`，`wait`或`then`将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)调用默认构造任务时的异常。

通过 `task_completion_event` 创建的任务将在设置任务完成事件后完成（并安排好其延续）。

采用取消标记的构造函数的版本可创建能够通过使用提供标记的 `cancellation_token_source` 取消的任务。 创建时没有使用取消标记的任务不可取消。

通过 `Windows::Foundation::IAsyncInfo` 接口或返回 `IAsyncInfo` 接口的 lambda 创建的任务在封闭的 Windows 运行时异步操作或行为完成时达到其终止状态。 同样，通过返回 `task<result_type>` 的 lamda 创建的任务在内部任务达到其终止状态时而非 lamda 返回时达到其终止状态。

`task` 行为与智能指针的行为类似，可按值安全传递。 它可以由多个线程访问，而无需锁定。

采用 Windows::Foundation::IAsyncInfo 接口或返回此类接口的 lambda 的构造函数重载才适用于 Windows 运行时应用。

有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

##  <a name="then"></a> 然后

向此任务添加延续任务。

```
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

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
用于指定执行延续的位置的变量。 此变量是仅在 UWP 应用中使用时很有用。 有关详细信息，请参阅[task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>返回值

新创建的延续任务。 返回任务的结果类型取决于 `_Func` 返回的内容。

### <a name="remarks"></a>备注

重载`then`的 lambda 或仿函数，返回 Windows::Foundation::IAsyncInfo 接口，仅可供 Windows 运行时应用。

有关如何使用任务延续构成异步工作的详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

##  <a name="wait"></a> 等待

等待此任务到达终止状态。 `wait` 可执行内联任务，前提是所有任务依赖项得到满足并且后台辅助线程没有选取它执行。

```
task_status wait() const;
```

### <a name="return-value"></a>返回值

可为 `task_status` 或 `completed` 的 `canceled` 值。 如果任务在执行期间遇到了异常或异常从前面的任务传播到此任务，则 `wait` 将引发该异常。

### <a name="remarks"></a>备注

> [!IMPORTANT]
>  在通用 Windows 平台 (UWP) 应用中，不要调用`wait`中的用户界面线程运行的代码。 否则，运行时会引发 [concurrency::invalid_operation](invalid-operation-class.md) ，原因是此方法阻止当前线程并可能导致应用停止响应。 但是，你可以调用 [concurrency::task::get](#get) 方法来接收基于任务的延续中的先行任务的结果。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
