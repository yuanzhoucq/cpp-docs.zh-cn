---
title: structured_task_group 类
ms.date: 11/04/2016
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
ms.openlocfilehash: 93dd79b755f79dcb4857c1b1c4856362b0bd45dd
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142636"
---
# <a name="structured_task_group-class"></a>structured_task_group 类

`structured_task_group` 类表示并行工作的高度结构化集合。 可以使用 `structured_task_group` 对象将各个并行任务排队到 `task_handle` 并等待它们完成，或在它们完成执行之前取消任务组，这将中止尚未开始执行的所有任务。

## <a name="syntax"></a>语法

```cpp
class structured_task_group;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[structured_task_group](#ctor)|已重载。 构造新的 `structured_task_group` 对象。|
|[~ structured_task_group 析构函数](#dtor)|销毁 `structured_task_group` 对象。 在执行析构函数之前，应调用对象上的 `wait` 或 `run_and_wait` 方法，除非由于异常导致析构函数作为堆栈展开的结果而执行。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[cancel](#cancel)|尽力尝试取消此任务组中根的工作的子树。 如果可能，在任务组上计划的每个任务都将以可传递的取消。|
|[is_canceling](#is_canceling)|向调用方通知任务组当前是否正在取消。 这并不一定表示对 `structured_task_group` 对象调用了 `cancel` 方法（不过，这种方法当然会使此方法符合返回**true 的条件**）。 这种情况可能是 `structured_task_group` 对象正在内联执行，而工作树中的某个任务组已取消。 在此类情况下，运行时可以提前确定取消将通过此 `structured_task_group` 对象的时间，也将返回**true** 。|
|[run](#run)|已重载。 计划 `structured_task_group` 对象上的任务。 调用方管理 `_Task_handle` 参数中传递的 `task_handle` 对象的生存期。 采用参数 `_Placement` 的版本会导致任务偏向在该参数指定的位置执行。|
|[run_and_wait](#run_and_wait)|已重载。 计划要在调用上下文上以内联方式运行的任务，并提供 `structured_task_group` 对象的帮助以实现完全取消支持。 如果 `task_handle` 对象作为参数传递给 `run_and_wait`，则调用方负责管理 `task_handle` 对象的生存期。 然后，该函数将等待，直到已完成或取消 `structured_task_group` 对象上的所有工作。|
|[再](#wait)|等待 `structured_task_group` 上的所有工作完成或取消。|

## <a name="remarks"></a>备注

对 `structured_task_group` 对象的使用有很多严重限制，以获得性能：

- 单个 `structured_task_group` 对象不能由多个线程使用。 `structured_task_group` 对象上的所有操作都必须由创建该对象的线程来执行。 此规则的两个例外情况是 `cancel` 和 `is_canceling`成员函数。 对象可能不在 lambda 表达式的捕获列表中，并可在任务中使用，除非该任务使用了取消操作之一。

- 计划给 `structured_task_group` 对象的所有任务都是通过使用 `task_handle` 对象计划的，必须显式管理的生存期。

- 只能按绝对嵌套顺序使用多个组。 如果声明了两个 `structured_task_group` 的对象，则声明的第二个对象（内部）在第一个方法（外部方法除外）上调用除 `cancel` 或 `is_canceling` 之外的任何方法之前都必须析构。 这种情况在这种情况下，只需在相同或有功能的嵌套范围内声明多个 `structured_task_group` 对象，以及通过 `run` 或 `run_and_wait` 方法在 `structured_task_group` 排队的任务的情况下，就是如此。

- 与常规 `task_group` 类不同，`structured_task_group` 类中的所有状态均为最终状态。 已将任务排队到组并等待它们完成后，你可能不会再次使用同一个组。

有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`structured_task_group`

## <a name="requirements"></a>要求

**标头：** ppl。h

**命名空间：** 并发

## <a name="cancel"></a>取消

尽力尝试取消此任务组中根的工作的子树。 如果可能，在任务组上计划的每个任务都将以可传递的取消。

```cpp
void cancel();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。

## <a name="is_canceling"></a>is_canceling

向调用方通知任务组当前是否正在取消。 这并不一定表示对 `structured_task_group` 对象调用了 `cancel` 方法（不过，这种方法当然会使此方法符合返回**true 的条件**）。 这种情况可能是 `structured_task_group` 对象正在内联执行，而工作树中的某个任务组已取消。 在此类情况下，运行时可以提前确定取消将通过此 `structured_task_group` 对象的时间，也将返回**true** 。

```cpp
bool is_canceling();
```

### <a name="return-value"></a>返回值

指示 `structured_task_group` 对象是否正在取消（或在不久后被保证）。

### <a name="remarks"></a>备注

有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。

## <a name="run"></a>用

计划 `structured_task_group` 对象上的任务。 调用方管理 `_Task_handle` 参数中传递的 `task_handle` 对象的生存期。 采用参数 `_Placement` 的版本会导致任务偏向在该参数指定的位置执行。

```cpp
template<class _Function>
void run(
    task_handle<_Function>& _Task_handle);

template<class _Function>
void run(
    task_handle<_Function>& _Task_handle,
    location& _Placement);
```

### <a name="parameters"></a>参数

*_Function*<br/>
将调用以执行任务句柄的主体的函数对象的类型。

*_Task_handle*<br/>
所计划的工作的句柄。 请注意，调用方负责此对象的生存期。 在对此 `structured_task_group` 对象调用 `wait` 或 `run_and_wait` 方法之前，运行时将继续预期它处于活动状态。

*_Placement*<br/>
对应执行 `_Task_handle` 参数所表示任务的位置的引用。

### <a name="remarks"></a>备注

运行时创建您传递给此方法的工作函数的副本。 传递给此方法的函数对象中发生的任何状态更改都不会出现在该函数对象的副本中。

如果 `structured_task_group` destructs 作为堆栈展开的结果，则不需要确保已对 `wait` 或 `run_and_wait` 方法进行了调用。 在这种情况下，析构函数将适当取消并等待 `_Task_handle` 参数表示的任务完成。

如果 `_Task_handle` 参数给定的任务句柄已通过 `run` 方法安排到任务组对象上，并且没有对该任务组的 `wait` 或 `run_and_wait` 方法的干预调用，则会引发[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)异常。

## <a name="run_and_wait"></a>run_and_wait

计划要在调用上下文上以内联方式运行的任务，并提供 `structured_task_group` 对象的帮助以实现完全取消支持。 如果 `task_handle` 对象作为参数传递给 `run_and_wait`，则调用方负责管理 `task_handle` 对象的生存期。 然后，该函数将等待，直到已完成或取消 `structured_task_group` 对象上的所有工作。

```cpp
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>参数

*_Function*<br/>
将调用以执行任务的函数对象的类型。

*_Task_handle*<br/>
将在调用上下文中以内联方式运行的任务的句柄。 请注意，调用方负责此对象的生存期。 在 `run_and_wait` 方法完成执行之前，运行时将继续预期它处于活动状态。

*_Func*<br/>
将调用以调用工作正文的函数。 这可能是 lambda 或其他对象，它支持具有签名 `void operator()()`的函数调用运算符的版本。

### <a name="return-value"></a>返回值

指示是否满足等待或任务组已取消，原因是显式取消操作或从其任务之一引发的异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>备注

请注意，计划给此 `structured_task_group` 对象的一个或多个任务可能会在调用上下文中以内联方式执行。

如果计划给此 `structured_task_group` 对象的一个或多个任务引发异常，则运行时将选择一个此类异常，并将其传播到对 `run_and_wait` 方法的调用。

返回此函数后，`structured_task_group` 对象被视为处于最终状态，并且不应使用。 请注意，`run_and_wait` 方法返回后的使用率将导致未定义的行为。

在执行的非异常路径中，你有权在执行 `structured_task_group` 的析构函数之前调用此方法或 `wait` 方法。

## <a name="ctor"></a>structured_task_group

构造新的 `structured_task_group` 对象。

```cpp
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>参数

*_CancellationToken*<br/>
要与此结构化任务组关联的取消标记。 取消标记时，将取消结构化任务组。

### <a name="remarks"></a>备注

采用取消标记的构造函数会创建一个在取消与标记相关联的源时将会取消的 `structured_task_group`。 提供显式取消标记还会隔离此结构化任务组，使其不会从具有不同令牌或无令牌的父组参与隐式取消。

## <a name="dtor"></a>~ structured_task_group

销毁 `structured_task_group` 对象。 在执行析构函数之前，应调用对象上的 `wait` 或 `run_and_wait` 方法，除非由于异常导致析构函数作为堆栈展开的结果而执行。

```cpp
~structured_task_group();
```

### <a name="remarks"></a>备注

如果析构函数作为正常执行的结果（例如，由于异常而不是堆栈展开 `run_and_wait` `wait`）运行，则析构函数可能引发[missing_wait](missing-wait-class.md)异常。

## <a name="wait"></a>再

等待 `structured_task_group` 上的所有工作完成或取消。

```cpp
task_group_status wait();
```

### <a name="return-value"></a>返回值

指示是否满足等待或任务组已取消，原因是显式取消操作或从其任务之一引发的异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>备注

请注意，计划给此 `structured_task_group` 对象的一个或多个任务可能会在调用上下文中以内联方式执行。

如果计划给此 `structured_task_group` 对象的一个或多个任务引发异常，则运行时将选择一个此类异常，并将其传播到对 `wait` 方法的调用。

返回此函数后，`structured_task_group` 对象被视为处于最终状态，并且不应使用。 请注意，`wait` 方法返回后的使用率将导致未定义的行为。

在执行的非异常路径中，你有权在执行 `structured_task_group` 的析构函数之前调用此方法或 `run_and_wait` 方法。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[task_group 类](task-group-class.md)<br/>
[task_handle 类](task-handle-class.md)
