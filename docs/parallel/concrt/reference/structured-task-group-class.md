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
ms.openlocfilehash: 44fd2a42f4c98a569e985449f0c55102a9cbc3a6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231671"
---
# <a name="structured_task_group-class"></a>structured_task_group 类

`structured_task_group` 类表示并行工作的高度结构化集合。 可以使用 `task_handle` 对象将各个并行任务排队到 `structured_task_group` 并等待它们完成，或在它们完成执行之前取消任务组，这将中止尚未开始执行的所有任务。

## <a name="syntax"></a>语法

```cpp
class structured_task_group;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[structured_task_group](#ctor)|已重载。 构造新的 `structured_task_group` 对象。|
|[~ structured_task_group 析构函数](#dtor)|销毁 `structured_task_group` 对象。 在 `wait` `run_and_wait` 析构函数执行之前，应调用对象上的或方法，除非由于异常导致析构函数作为堆栈展开的结果而执行。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[cancel](#cancel)|尽力尝试取消此任务组中根的工作的子树。 如果可能，在任务组上计划的每个任务都将以可传递的取消。|
|[is_canceling](#is_canceling)|向调用方通知任务组当前是否正在取消。 这并不一定表示对 `cancel` 对象调用了方法（不过，这种方法当然会要求 `structured_task_group` 返回此方法 **`true`** ）。 这可能是因为 `structured_task_group` 对象正在内联执行，而工作树中的某个任务组已取消。 如果在这种情况下，运行时可以提前确定取消将流经此对象的时间 `structured_task_group` ， **`true`** 也将返回。|
|[用](#run)|已重载。 在对象上计划任务 `structured_task_group` 。 调用方管理 `task_handle` 参数中传递的对象的生存期 `_Task_handle` 。 采用参数 `_Placement` 的版本会导致任务偏向在该参数指定的位置执行。|
|[run_and_wait](#run_and_wait)|已重载。 计划在调用上下文上以内联方式运行的任务，并提供 `structured_task_group` 完全取消支持的对象的帮助。 如果 `task_handle` 对象作为参数传递给 `run_and_wait` ，则调用方负责管理该对象的生存期 `task_handle` 。 然后，该函数会等待，直到对象上的所有工作都已 `structured_task_group` 完成或已取消。|
|[再](#wait)|等待，直到上的所有工作 `structured_task_group` 都已完成或被取消。|

## <a name="remarks"></a>备注

对对象的使用有很多严重限制 `structured_task_group` ，以获得性能：

- 单个 `structured_task_group` 对象不能由多个线程使用。 对象上的所有操作都 `structured_task_group` 必须由创建该对象的线程来执行。 此规则的两个例外情况是成员函数 `cancel` 和 `is_canceling` 。 对象可能不在 lambda 表达式的捕获列表中，并可在任务中使用，除非该任务使用了取消操作之一。

- 计划对象的所有任务 `structured_task_group` 都是通过使用 `task_handle` 必须显式管理生存期的对象进行计划的。

- 只能按绝对嵌套顺序使用多个组。 如果声明了两个 `structured_task_group` 对象，则声明的第二个对象（内部）必须在除 `cancel` 或 `is_canceling` 在第一个方法（外部方法除外）以外的任何方法之前析构。 这种情况在这种情况下，只需在 `structured_task_group` 相同或功能的嵌套范围内声明多个对象，以及 `structured_task_group` 通过或方法排队到的任务的情况下，就是如此 `run` `run_and_wait` 。

- 与一般 `task_group` 类不同，类中的所有状态 `structured_task_group` 都是最终的。 已将任务排队到组并等待它们完成后，你可能不会再次使用同一个组。

有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`structured_task_group`

## <a name="requirements"></a>要求

**标头：** ppl。h

**命名空间：** 并发

## <a name="cancel"></a><a name="cancel"></a>取消

尽力尝试取消此任务组中根的工作的子树。 如果可能，在任务组上计划的每个任务都将以可传递的取消。

```cpp
void cancel();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。

## <a name="is_canceling"></a><a name="is_canceling"></a>is_canceling

向调用方通知任务组当前是否正在取消。 这并不一定表示对 `cancel` 对象调用了方法（不过，这种方法当然会要求 `structured_task_group` 返回此方法 **`true`** ）。 这可能是因为 `structured_task_group` 对象正在内联执行，而工作树中的某个任务组已取消。 如果在这种情况下，运行时可以提前确定取消将流经此对象的时间 `structured_task_group` ， **`true`** 也将返回。

```cpp
bool is_canceling();
```

### <a name="return-value"></a>返回值

指示 `structured_task_group` 对象是否正在取消（或在短期内）的指示。

### <a name="remarks"></a>备注

有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。

## <a name="run"></a><a name="run"></a>用

在对象上计划任务 `structured_task_group` 。 调用方管理 `task_handle` 参数中传递的对象的生存期 `_Task_handle` 。 采用参数 `_Placement` 的版本会导致任务偏向在该参数指定的位置执行。

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
所计划的工作的句柄。 请注意，调用方负责此对象的生存期。 在 `wait` `run_and_wait` 此对象上调用或方法之前，运行时将继续预期它处于活动状态 `structured_task_group` 。

*_Placement*<br/>
对应执行 `_Task_handle` 参数所表示任务的位置的引用。

### <a name="remarks"></a>备注

运行时创建您传递给此方法的工作函数的副本。 传递给此方法的函数对象中发生的任何状态更改都不会出现在该函数对象的副本中。

如果 `structured_task_group` destructs 是从异常堆栈展开的结果，则无需确保已对或方法进行了调用 `wait` `run_and_wait` 。 在这种情况下，析构函数将适当取消并等待由参数表示的任务 `_Task_handle` 完成。

如果已[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)通过方法将参数给定的任务句柄 `_Task_handle` 安排到任务组对象 `run` 上，并且没有对 `wait` `run_and_wait` 该任务组的或方法的干预调用，则会引发 invalid_multiple_scheduling 异常。

## <a name="run_and_wait"></a><a name="run_and_wait"></a>run_and_wait

计划在调用上下文上以内联方式运行的任务，并提供 `structured_task_group` 完全取消支持的对象的帮助。 如果 `task_handle` 对象作为参数传递给 `run_and_wait` ，则调用方负责管理该对象的生存期 `task_handle` 。 然后，该函数会等待，直到对象上的所有工作都已 `structured_task_group` 完成或已取消。

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
将在调用上下文中以内联方式运行的任务的句柄。 请注意，调用方负责此对象的生存期。 在方法完成执行之前，运行时将继续预期它处于活动状态 `run_and_wait` 。

*_Func*<br/>
将调用以调用工作正文的函数。 这可能是 lambda 或其他对象，它支持具有签名的函数调用运算符的版本 `void operator()()` 。

### <a name="return-value"></a>返回值

指示是否满足等待或任务组已取消，原因是显式取消操作或从其任务之一引发的异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>备注

请注意，计划给此对象的一个或多个任务 `structured_task_group` 可能会在调用上下文中以内联方式执行。

如果计划给此对象的一个或多个任务 `structured_task_group` 引发异常，则运行时将选择一个此类异常，并将其传播到对方法的调用 `run_and_wait` 。

返回此函数后，`structured_task_group` 对象被视为处于最终状态，并且不应使用。 请注意，该方法返回后的使用率 `run_and_wait` 将导致未定义的行为。

在执行的非异常路径中，你有权在执行的析构函数之前调用此方法或 `wait` 方法 `structured_task_group` 。

## <a name="structured_task_group"></a><a name="ctor"></a>structured_task_group

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

## <a name="structured_task_group"></a><a name="dtor"></a>~ structured_task_group

销毁 `structured_task_group` 对象。 在 `wait` `run_and_wait` 析构函数执行之前，应调用对象上的或方法，除非由于异常导致析构函数作为堆栈展开的结果而执行。

```cpp
~structured_task_group();
```

### <a name="remarks"></a>备注

如果析构函数作为正常执行的结果（例如，由于异常而不是堆栈展开）运行，则 `wait` `run_and_wait` 析构函数可能引发[missing_wait](missing-wait-class.md)异常。

## <a name="wait"></a><a name="wait"></a>再

等待，直到上的所有工作 `structured_task_group` 都已完成或被取消。

```cpp
task_group_status wait();
```

### <a name="return-value"></a>返回值

指示是否满足等待或任务组已取消，原因是显式取消操作或从其任务之一引发的异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>备注

请注意，计划给此对象的一个或多个任务 `structured_task_group` 可能会在调用上下文中以内联方式执行。

如果计划给此对象的一个或多个任务 `structured_task_group` 引发异常，则运行时将选择一个此类异常，并将其传播到对方法的调用 `wait` 。

返回此函数后，`structured_task_group` 对象被视为处于最终状态，并且不应使用。 请注意，该方法返回后的使用率 `wait` 将导致未定义的行为。

在执行的非异常路径中，你有权在执行的析构函数之前调用此方法或 `run_and_wait` 方法 `structured_task_group` 。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[task_group 类](task-group-class.md)<br/>
[task_handle 类](task-handle-class.md)
