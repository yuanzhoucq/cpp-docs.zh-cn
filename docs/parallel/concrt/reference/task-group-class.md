---
title: task_group 类
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 60c147f38ddc3936f47aea0cfd1ab1548b382441
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142568"
---
# <a name="task_group-class"></a>task_group 类

`task_group` 类表示可以等待或取消的并行工作的集合。

## <a name="syntax"></a>语法

```cpp
class task_group;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[task_group](#ctor)|已重载。 构造新的 `task_group` 对象。|
|[~ task_group 析构函数](#dtor)|销毁 `task_group` 对象。 在执行析构函数之前，应调用对象上的 `wait` 或 `run_and_wait` 方法，除非析构函数作为堆栈展开由于异常的结果而执行。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[cancel](#cancel)|尽力尝试取消此任务组中根的工作的子树。 如果可能，在任务组上计划的每个任务都将以可传递的取消。|
|[is_canceling](#is_canceling)|向调用方通知任务组当前是否正在取消。 这并不一定表示对 `task_group` 对象调用了 `cancel` 方法（不过，这种方法当然会使此方法符合 `true`）。 这种情况可能是 `task_group` 对象正在内联执行，而工作树中的某个任务组已取消。 在此类情况下，运行时可以提前确定取消将通过此 `task_group` 对象的时间，也将返回 `true`。|
|[run](#run)|已重载。 计划 `task_group` 对象上的任务。 如果 `task_handle` 对象作为参数传递给 `run`，则调用方负责管理 `task_handle` 对象的生存期。 采用函数对象作为参数的方法的版本涉及到运行时中的堆分配，这可能比使用采用对 `task_handle` 对象的引用的版本更好。 采用参数 `_Placement` 的版本导致任务偏向在该参数指定的位置执行。|
|[run_and_wait](#run_and_wait)|已重载。 计划要在调用上下文上以内联方式运行的任务，并提供 `task_group` 对象的帮助以实现完全取消支持。 然后，该函数将等待，直到已完成或取消 `task_group` 对象上的所有工作。 如果 `task_handle` 对象作为参数传递给 `run_and_wait`，则调用方负责管理 `task_handle` 对象的生存期。|
|[再](#wait)|一直等到 `task_group` 对象上的所有工作都已完成或已取消。|

## <a name="remarks"></a>备注

与严重限制 `structured_task_group` 类不同，`task_group` 类更通用。 它没有[structured_task_group](structured-task-group-class.md)描述的任何限制。 `task_group` 对象可以安全地在线程之间使用，并可通过自由格式方式使用。 `task_group` 构造的缺点是，它可能不会执行，也不能用于执行少量工作的任务的 `structured_task_group` 构造。

有关详细信息，请参阅[任务并行](../task-parallelism-concurrency-runtime.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`task_group`

## <a name="requirements"></a>要求

**标头：** ppl。h

**命名空间：** 并发

## <a name="cancel"></a>取消

尽力尝试取消此任务组中根的工作的子树。 如果可能，在任务组上计划的每个任务都将以可传递的取消。

```cpp
void cancel();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[取消](../cancellation-in-the-ppl.md)。

## <a name="is_canceling"></a>is_canceling

向调用方通知任务组当前是否正在取消。 这并不一定表示对 `task_group` 对象调用了 `cancel` 方法（不过，这种方法当然会使此方法符合 `true`）。 这种情况可能是 `task_group` 对象正在内联执行，而工作树中的某个任务组已取消。 在此类情况下，运行时可以提前确定取消将通过此 `task_group` 对象的时间，也将返回 `true`。

```cpp
bool is_canceling();
```

### <a name="return-value"></a>返回值

指示 `task_group` 对象是否正在取消（或在不久后被保证）。

### <a name="remarks"></a>备注

有关详细信息，请参阅[取消](../cancellation-in-the-ppl.md)。

## <a name="run"></a>用

计划 `task_group` 对象上的任务。 如果 `task_handle` 对象作为参数传递给 `run`，则调用方负责管理 `task_handle` 对象的生存期。 采用函数对象作为参数的方法的版本涉及到运行时中的堆分配，这可能比使用采用对 `task_handle` 对象的引用的版本更好。 采用参数 `_Placement` 的版本导致任务偏向在该参数指定的位置执行。

```cpp
template<
   typename _Function
>
void run(
   const _Function& _Func
);

template<
   typename _Function
>
void run(
   const _Function& _Func,
   location& _Placement
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle,
   location& _Placement
);
```

### <a name="parameters"></a>参数

*_Function*<br/>
将调用以执行任务句柄的主体的函数对象的类型。

*_Func*<br/>
将调用以调用任务正文的函数。 这可能是 lambda 表达式或支持 `void operator()()`的函数调用运算符版本的其他对象。

*_Placement*<br/>
对应执行 `_Func` 参数所表示任务的位置的引用。

*_Task_handle*<br/>
所计划的工作的句柄。 请注意，调用方负责此对象的生存期。 在对此 `task_group` 对象调用 `wait` 或 `run_and_wait` 方法之前，运行时将继续预期它处于活动状态。

### <a name="remarks"></a>备注

运行时计划所提供的工作函数稍后运行，这可以在调用函数返回之后运行。 此方法使用[task_handle](task-handle-class.md)对象保存提供的工作函数的副本。 因此，您传递给此方法的函数对象中发生的任何状态更改都不会出现在该函数对象的副本中。 此外，请确保在工作函数返回之前，通过指针或对工作函数的引用传递的任何对象的生存期保持有效。

如果 `task_group` destructs 作为堆栈展开的结果，则不需要确保已对 `wait` 或 `run_and_wait` 方法进行了调用。 在这种情况下，析构函数将适当取消并等待 `_Task_handle` 参数表示的任务完成。

如果 `_Task_handle` 参数给定的任务句柄已通过 `run` 方法安排到任务组对象上，并且没有对该任务组的 `wait` 或 `run_and_wait` 方法的干预调用，则该方法将引发[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)异常。

## <a name="run_and_wait"></a>run_and_wait

计划要在调用上下文上以内联方式运行的任务，并提供 `task_group` 对象的帮助以实现完全取消支持。 然后，该函数将等待，直到已完成或取消 `task_group` 对象上的所有工作。 如果 `task_handle` 对象作为参数传递给 `run_and_wait`，则调用方负责管理 `task_handle` 对象的生存期。

```cpp
template<
   class _Function
>
task_group_status run_and_wait(
   task_handle<_Function>& _Task_handle
);

template<
   class _Function
>
task_group_status run_and_wait(
   const _Function& _Func
);
```

### <a name="parameters"></a>参数

*_Function*<br/>
将调用以执行任务主体的函数对象的类型。

*_Task_handle*<br/>
将在调用上下文中以内联方式运行的任务的句柄。 请注意，调用方负责此对象的生存期。 在 `run_and_wait` 方法完成执行之前，运行时将继续预期它处于活动状态。

*_Func*<br/>
将调用以调用工作正文的函数。 这可能是 lambda 表达式或支持 `void operator()()`的函数调用运算符版本的其他对象。

### <a name="return-value"></a>返回值

指示是否满足等待或任务组已取消，原因是显式取消操作或从其任务之一引发的异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md#task_group_status)。

### <a name="remarks"></a>备注

请注意，计划给此 `task_group` 对象的一个或多个任务可能会在调用上下文中以内联方式执行。

如果计划给此 `task_group` 对象的一个或多个任务引发异常，则运行时将选择一个此类异常，并将其传播到对 `run_and_wait` 方法的调用。

当从 `task_group` 对象的 `run_and_wait` 方法返回时，运行时将对象重置为可重复使用的干净状态。 这包括取消 `task_group` 对象的情况。

在执行的非异常路径中，你有权在执行 `task_group` 的析构函数之前调用此方法或 `wait` 方法。

## <a name="ctor"></a>task_group

构造新的 `task_group` 对象。

```cpp
task_group();

task_group(
   cancellation_token _CancellationToken
);
```

### <a name="parameters"></a>参数

*_CancellationToken*<br/>
与此任务组相关联的取消标记。 取消标记时，也将取消此任务组。

### <a name="remarks"></a>备注

采用取消标记的构造函数会创建一个在取消与标记相关联的源时将会取消的 `task_group`。 提供显式取消标记也可以避免此任务组参与采用不同标记或没有标记的父组的隐式取消。

## <a name="dtor"></a>~ task_group

销毁 `task_group` 对象。 在执行析构函数之前，应调用对象上的 `wait` 或 `run_and_wait` 方法，除非析构函数作为堆栈展开由于异常的结果而执行。

```cpp
~task_group();
```

### <a name="remarks"></a>备注

如果析构函数作为正常执行的结果（例如，由于异常而不是堆栈展开 `run_and_wait` `wait`）运行，则析构函数可能引发[missing_wait](missing-wait-class.md)异常。

## <a name="wait"></a>再

一直等到 `task_group` 对象上的所有工作都已完成或已取消。

```cpp
task_group_status wait();
```

### <a name="return-value"></a>返回值

指示是否满足等待或任务组已取消，原因是显式取消操作或从其任务之一引发的异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md#task_group_status)。

### <a name="remarks"></a>备注

请注意，计划给此 `task_group` 对象的一个或多个任务可能会在调用上下文中以内联方式执行。

如果计划给此 `task_group` 对象的一个或多个任务引发异常，则运行时将选择一个此类异常，并将其传播到对 `wait` 方法的调用。

对 `task_group` 对象调用 `wait` 会将其重置为可重复使用的干净状态。 这包括取消 `task_group` 对象的情况。

在执行的非异常路径中，你有权在执行 `task_group` 的析构函数之前调用此方法或 `run_and_wait` 方法。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[structured_task_group 类](structured-task-group-class.md)<br/>
[task_handle 类](task-handle-class.md)
