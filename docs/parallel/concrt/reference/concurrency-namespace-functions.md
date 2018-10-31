---
title: 并发命名空间函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- concrt/concurrency::Alloc
- concrt/concurrency::DisableTracing
- concrt/concurrency::EnableTracing
- concrtrm/concurrency::GetExecutionContextId
- concrtrm/concurrency::GetOSVersion
- concrtrm/concurrency::GetProcessorNodeCount
- concrtrm/concurrency::GetSchedulerId
- agents/concurrency::asend
- ppltasks/concurrency::cancel_current_task
- ppltasks/concurrency::create_async
- ppltasks/concurrency::create_task
- concurrent_vector/concurrency::internal_assign_iterators
- ppl/concurrency::interruption_point
- agents/concurrency::make_choice
- agents/concurrency::make_greedy_join
- ppl/concurrency::make_task
- ppl/concurrency::parallel_buffered_sort
- ppl/concurrency::parallel_for_each
- ppl/concurrency::parallel_invoke
- ppl/concurrency::parallel_reduce
- ppl/concurrency::parallel_sort
- agents/concurrency::receive
- ppl/concurrency::run_with_cancellation_token
- pplconcrt/concurrency::set_ambient_scheduler
- concrt/concurrency::set_task_execution_resources
- ppltasks/concurrency::task_from_exception
- ppltasks/concurrency::task_from_result
- concrt/concurrency::wait
- ppltasks/concurrency::when_all
- ppltasks/concurrency::when_any
dev_langs:
- C++
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b89c1a3057e9753b99aaac837c903b6fd5f6d3ea
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163343"
---
# <a name="concurrency-namespace-functions"></a>并发命名空间函数

||||
|-|-|-|
|[分配](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing](#disabletracing)|
|[EnableTracing](#enabletracing)|[免费](#free)|[GetExecutionContextId](#getexecutioncontextid)|
|[GetOSVersion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|
|[cancel_current_task](#cancel_current_task)|[clear](#clear)|[create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[receive](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[发送](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[等待](#wait)|
|[when_all](#when_all)|[when_any](#when_any)|

##  <a name="alloc"></a>  分配

通过并发运行时缓存子分配器分配具有指定大小的内存块。

```
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>参数

*_NumBytes*<br/>
要分配的内存字节数。

### <a name="return-value"></a>返回值

指向新分配的内存的指针。

### <a name="remarks"></a>备注

有关哪些应用程序中的方案适合使用缓存子分配器的详细信息，请参阅[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

##  <a name="asend"></a>  asend

异步发送操作，计划任务以将数据传播到目标块。

```
template <class T>
bool asend(
    _Inout_ ITarget<T>* _Trg,
    const T& _Data);

template <class T>
bool asend(
    ITarget<T>& _Trg,
    const T& _Data);
```

### <a name="parameters"></a>参数

*T*<br/>
要发送的数据的类型。

*_Trg*<br/>
指针或向其发送数据的目标引用。

*数据 （_d)*<br/>
对要发送的数据的引用。

### <a name="return-value"></a>返回值

**true**接受该消息之前的方法返回时，如果**false**否则为。

### <a name="remarks"></a>备注

有关详细信息，请参阅[消息传递函数](../../../parallel/concrt/message-passing-functions.md)。

##  <a name="cancel_current_task"></a>  cancel_current_task

获取当前执行的任务。 此函数可从任务主体中进行调用，以便中止任务的执行并使其进入 `canceled` 状态。

不支持从 `task` 主体外部调用此函数的情况。 这样做将导致未定义的行为，例如应用程序崩溃或挂起。

```
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

##  <a name="clear"></a>  清除

清除并发队列，销毁所有当前排入队列的元素。 此方法不是并发安全的。

```
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>参数

*T*<br/>

*_Ax*<br/>

##  <a name="create_async"></a>  create_async

基于用户提供的 lambda 或函数对象创建 Windows 运行时异步构造。 `create_async` 的返回类型是基于传递给方法的 lambda 的签名的 `IAsyncAction^`、`IAsyncActionWithProgress<TProgress>^`、`IAsyncOperation<TResult>^` 或 `IAsyncOperationWithProgress<TResult, TProgress>^` 之一。

```
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>参数

*_Function*<br/>
类型。

*_Func*<br/>
从其中创建 Windows 运行时异步构造的 lambda 或函数对象。

### <a name="return-value"></a>返回值

一个异步构造，它由 IAsyncAction ^、 IAsyncActionWithProgress\<TProgress > ^，IAsyncOperation\<TResult > ^，或 IAsyncOperationWithProgress\<，TProgress > ^。 返回的接口依赖于传递给函数的 lambda 的签名。

### <a name="remarks"></a>备注

lambda 的返回类型确定该构造是一个行为还是一项操作。

返回 void 的 lambda 将导致创建一些行为。 返回类型为 `TResult` 的结果的 lambda 将导致创建 TResult 的操作。

lambda 可能还返回 `task<TResult>`（在自身中封装异步工作或是表示异步工作的任务链的延续）。 在此示例中，由于任务是异步执行的，所以将以内联方式执行 lambda，并且将解包 lambda 的返回类型以生成 `create_async` 返回的异步构造。 这意味着，lambda 返回 task\<void > 将导致的操作，并返回一个任务的 lambda 创建\<TResult > 将导致创建 TResult 操作。

lambda 可采用零个、一个或两个自变量。 有效的参数是 `progress_reporter<TProgress>` 和 `cancellation_token`（此顺序为同时使用两个参数的顺序）。 无自变量的 lambda 将导致创建一个缺少进度报告功能的异步构造。 Lambda 采用 progress_reporter\<TProgress > 将导致`create_async`要返回的异步构造将报告 TProgress 类型的进度每次`report`调用 progress_reporter 对象的方法。 采用 cancellation_token 的 lambda 可以使用该标记来检查取消情况，或将该标记传递给它创建的任务，以便取消异步构造可导致取消这些任务。

如果 lambda 或函数对象的主体返回的结果 (并且不是 task\<TResult >)，则将为其隐式创建的任务运行时上下文中的 MTA 在过程内以异步方式执行。 `IAsyncInfo::Cancel` 方法将导致取消隐式任务。

如果 lambda 的主体返回一个任务，则 lamba 将通过声明 lambda 采用类型为 `cancellation_token` 的参数，以内联方式执行，您可以通过在创建任务时将此标记传入，从而触发对在 lambda 中创建的任何任务的取消。 您还可对此标记使用 `register_callback` 方法，以使运行时在您对产生的异步操作或行为调用 `IAsyncInfo::Cancel` 时调用回调。

此函数是仅适用于 Windows 运行时应用。

##  <a name="createresourcemanager"></a>  CreateResourceManager

返回表示并发运行时的资源管理器的单一实例的接口。 资源管理器负责将资源分配给想要相互合作的计划程序。

```
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>返回值

一个 `IResourceManager` 接口。

### <a name="remarks"></a>备注

多个后续调用此方法将返回同一实例的资源管理器。 每次调用此方法会递增引用计数在资源管理器中，并必须通过调用匹配[iresourcemanager:: Release](iresourcemanager-structure.md)方法完成你的计划程序时使用资源管理器进行通信。

[unsupported_os](unsupported-os-class.md)如果操作系统不支持并发运行时引发。

##  <a name="create_task"></a>  create_task

创建 PPL[任务](task-class.md)对象。 在你会使用任务构造函数的任何位置都可以使用 `create_task`。 出于便利性提供该函数，因为它允许在创建任务时使用 `auto` 关键字。

```
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>参数

*T*<br/>
从中构造任务的参数的类型。

*_ReturnType*<br/>
类型。

*_Param*<br/>
从中构造任务的参数。 这可能是 lambda 或函数对象`task_completion_event`对象，另`task`对象或如果在 UWP 应用中使用任务 Windows::Foundation::IAsyncInfo 接口。

*_TaskOptions*<br/>
任务选项。

*_Task*<br/>
要创建的任务。

### <a name="return-value"></a>返回值

类型的新任务`T`，即从推断`_Param`。

### <a name="remarks"></a>备注

第一个重载的行为类似于采用单个参数的任务构造函数。

第二个重载将提供与新创建的任务的取消令牌相关联。 如果使用此重载不允许传入不同`task`对象作为第一个参数。

返回的任务的类型是从第一个参数推断函数。 如果`_Param`是`task_completion_event<T>`即`task<T>`，或返回任何一种类型的仿函数`T`或`task<T>`，创建的任务的类型是`task<T>`。

在 UWP 应用中，如果`_Param`属于类型 Windows::Foundation::IAsyncOperation\<T > ^ 或 Windows::Foundation::IAsyncOperationWithProgress\<T，P > ^，或创建的任务将为返回这些类型的仿函数，类型`task<T>`。 如果`_Param`属于类型 Windows::Foundation::IAsyncAction ^ 或 Windows::Foundation::IAsyncActionWithProgress\<P > ^，或返回这些类型的仿函数，创建的任务将具有键入`task<void>`。

##  <a name="disabletracing"></a>  DisableTracing

在并发运行时中禁用跟踪。 此函数被弃用，因为默认注销 ETW 跟踪。

```
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>返回值

如果已正确禁用跟踪，`S_OK`返回。 如果之前未启动跟踪，将返回 `E_NOT_STARTED`。

##  <a name="enabletracing"></a>  EnableTracing

在并发运行时中启用跟踪。 此函数被弃用，因为现在默认启用 ETW 跟踪。

```
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>返回值

如果正确启动跟踪，`S_OK`返回; 否则为`E_NOT_STARTED`返回。

##  <a name="free"></a>  免费

释放先前通过 `Alloc` 方法分配给并发运行时的缓存子分配器的内存块。

```
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>参数

*_PAllocation*<br/>
指向以前分配的内存的指针`Alloc`这是要释放的方法。 如果将参数`_PAllocation`设置为值`NULL`，此方法将忽略它并立即返回。

### <a name="remarks"></a>备注

有关哪些应用程序中的方案适合使用缓存子分配器的详细信息，请参阅[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

##  <a name="get_ambient_scheduler"></a>  get_ambient_scheduler

```
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>返回值

##  <a name="getexecutioncontextid"></a>  GetExecutionContextId

返回可以分配给实现 `IExecutionContext` 接口的执行上下文的唯一标识符。

```
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>返回值

执行上下文是唯一标识符。

### <a name="remarks"></a>备注

使用此方法以获取执行上下文的标识符之前传递`IExecutionContext`作为任一资源管理器提供方法的参数的接口。

##  <a name="getosversion"></a>  GetOSVersion

返回操作系统版本。

```
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>返回值

一个枚举的值，表示操作系统。

### <a name="remarks"></a>备注

[unsupported_os](unsupported-os-class.md)如果操作系统不支持并发运行时引发。

##  <a name="getprocessorcount"></a>  GetProcessorCount

返回基础系统上的硬件线程数。

```
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>返回值

硬件线程数。

### <a name="remarks"></a>备注

[unsupported_os](unsupported-os-class.md)如果操作系统不支持并发运行时引发。

##  <a name="getprocessornodecount"></a>  GetProcessorNodeCount

返回基础系统上的 NUMA 节点数或处理器包数。

```
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>返回值

NUMA 节点或处理器包数。

### <a name="remarks"></a>备注

如果系统包含多个 NUMA 节点比处理器包，则返回 NUMA 节点数，否则，返回处理器包数。

[unsupported_os](unsupported-os-class.md)如果操作系统不支持并发运行时引发。

##  <a name="getschedulerid"></a>  GetSchedulerId

返回可以分配给实现 `IScheduler` 接口的计划程序的唯一标识符。

```
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>返回值

计划程序的唯一标识符。

### <a name="remarks"></a>备注

使用此方法来为你的计划程序获取的标识符之前传递`IScheduler`作为任一资源管理器提供方法的参数的接口。

##  <a name="internal_assign_iterators"></a>  internal_assign_iterators

```
template<typename T, class _Ax>
template<class _I>
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```

### <a name="parameters"></a>参数

*T*<br/>

*_Ax*<br/>

*_I*<br/>

*first*<br/>

*最后一个*<br/>

##  <a name="interruption_point"></a>  interruption_point

创建取消的中断点。 如果正在调用此函数的上下文中执行取消操作，则此函数将引发内部异常，该内部异常中止当前执行并行工作的执行。 如果没有正在执行取消操作，则函数不执行任何操作。

```
inline void interruption_point();
```

### <a name="remarks"></a>备注

您不应捕捉由 `interruption_point()` 函数引发的内部取消异常。 此异常将由运行时捕捉和处理，捕捉它可能会导致程序行为异常。

##  <a name="is_current_task_group_canceling"></a>  is_current_task_group_canceling

返回在当前上下文中进行内联执行的任务组是否正处于活动取消的过程中（或不久将取消）的指示。 请注意，如果当前上下文中没有当前正在进行内联执行的任务组，则将返回 `false`。

```
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>返回值

**true**取消当前正在执行的任务组，如果**false**否则为。

### <a name="remarks"></a>备注

有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。

##  <a name="make_choice"></a>  make_choice

从可选的 `choice` 或 `Scheduler` 及两个或更多输入源构造 `ScheduleGroup` 消息块。

```
template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    Scheduler& _PScheduler,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    ScheduleGroup& _PScheduleGroup,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>参数

T1<br/>
第一个源消息块类型。

T2<br/>
第二个源消息块类型。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `choice` 对象。

*_Item1*<br/>
第一个源。

*_Item2*<br/>
第二个源。

*项目 （_i)*<br/>
其他源。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `choice` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="return-value"></a>返回值

一个具有两个或更多输入源的 `choice` 消息块。

##  <a name="make_greedy_join"></a>  make_greedy_join

从可选的 `greedy multitype_join` 或 `Scheduler` 及两个或更多输入源构造 `ScheduleGroup` 消息块。

```
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>,greedy> make_greedy_join(
    Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    T1 _Item1,
    T2 _Items,
    Ts... _Items);
```

### <a name="parameters"></a>参数

T1<br/>
第一个源消息块类型。

T2<br/>
第二个源消息块类型。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `multitype_join` 对象。

*_Item1*<br/>
第一个源。

*_Item2*<br/>
第二个源。

*项目 （_i)*<br/>
其他源。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `multitype_join` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="return-value"></a>返回值

一个具有两个或更多输入源的 `greedy multitype_join` 消息块。

##  <a name="make_join"></a>  make_join

从可选的 `non_greedy multitype_join` 或 `Scheduler` 及两个或更多输入源构造 `ScheduleGroup` 消息块。

```
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>>
    make_join(
Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>参数

T1<br/>
第一个源消息块类型。

T2<br/>
第二个源消息块类型。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `multitype_join` 对象。

*_Item1*<br/>
第一个源。

*_Item2*<br/>
第二个源。

*项目 （_i)*<br/>
其他源。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `multitype_join` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="return-value"></a>返回值

一个具有两个或更多输入源的 `non_greedy multitype_join` 消息块。

##  <a name="make_task"></a>  make_task

用于创建 `task_handle` 对象的工厂方法。

```
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>参数

*_Function*<br/>
将调用来执行工作所表示的函数对象的类型`task_handle`对象。

*_Func*<br/>
将调用来执行工作所表示的函数`task_handle`对象。 这可能是 lambda 函数，指向函数，也支持具有签名的函数调用运算符的版本的任何对象`void operator()()`。

### <a name="return-value"></a>返回值

一个 `task_handle` 对象。

### <a name="remarks"></a>备注

此函数时，您需要创建`task_handle`对象使用 lambda 表达式，因为它允许您不知道 lambda 函子的类型，则返回 true 的情况下创建该对象。

##  <a name="parallel_buffered_sort"></a>  parallel_buffered_sort

将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列（以并行方式）。 此函数是基于比较、不稳定的就地排序，因此它与 `std::sort` 在语义上相似，但它需要 `O(n)` 附加空间，并需要待排序的元素进行默认初始化。

```
template<typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>参数

*_Random_iterator*<br/>
输入范围的迭代器类型。

*_Allocator*<br/>
C + + 标准库兼容的内存分配器的类型。

*_Function*<br/>
二进制比较器的类型。

*（_b)*<br/>
一种随机访问迭代器，用于寻址要排序的范围中第一个元素的位置。

*（_e)*<br/>
一种随机访问迭代器，用于定址要排序的范围中最后元素之后下一个元素的位置。

*_Alloc*<br/>
C + + 标准库兼容的内存分配器的实例。

*_Func*<br/>
用户定义的谓词函数对象，定义排序中连续元素要满足的比较条件。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。 该比较器函数必须对序列中的元素对进行严格弱排序。

*_Chunk_size*<br/>
最小大小的区块将拆分为两个区块用于并行执行。

### <a name="remarks"></a>备注

所有重载都需要`n * sizeof(T)`附加空间，其中`n`是要进行排序的元素数和`T`是元素类型。 在大多数情况下 parallel_buffered_sort 将通过显示中的性能改进[parallel_sort](concurrency-namespace-functions.md)，应使用它通过 parallel_sort 如果有可用的内存。

如果不提供二进制比较运算符`std::less`用作默认情况下，需要提供操作员的元素类型`operator<()`。

如果未提供的分配器类型或实例，c + + 标准库内存分配器`std::allocator<T>`用于分配的缓冲区。

算法将输入范围分为两个区块，然后将每个区块分成两个以并行方式执行的子区块。 可选自变量 `_Chunk_size` 可用于向算法指示它应按顺序处理区块的大小 < `_Chunk_size`。

##  <a name="parallel_for"></a>  parallel_for

`parallel_for` 循环访问某个索引范围，并在每次迭代时以并行方式执行用户提供的函数。

```
template <typename _Index_type, typename _Function, typename _Partitioner>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func,
    _Partitioner&& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const static_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const simple_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    affinity_partitioner& _Part);
```

### <a name="parameters"></a>参数

*_Index_type*<br/>
所使用的迭代的索引的类型。

*_Function*<br/>
将在每次迭代执行的函数的类型。

*_Partitioner*<br/>
用于进行分区提供的范围分区程序的类型。

*first*<br/>
要包括在迭代中的第一个索引。

*最后一个*<br/>
索引一个过去的迭代中要包含的最后一个索引。

*_Step*<br/>
值，通过它来单步在迭代过程中从`first`到`last`。 在步骤必须是正数。 [invalid_argument](../../../standard-library/invalid-argument-class.md)的步骤是等于或大于 1 时引发。

*_Func*<br/>
在每次迭代执行的函数。 这可能是 lambda 表达式、 函数指针，也支持具有签名的函数调用运算符的版本的任何对象`void operator()(_Index_type)`。

*部件 （_p)*<br/>
对分区程序对象的引用。 参数可以是之一`const` [auto_partitioner](auto-partitioner-class.md)`&`， `const` [static_partitioner](static-partitioner-class.md)`&`， `const` [simple_分区程序](simple-partitioner-class.md)`&`或[affinity_partitioner](affinity-partitioner-class.md) `&`如果[affinity_partitioner](affinity-partitioner-class.md)对象，该引用必须是一个非常量左值引用，以便算法可以存储状态，供未来循环重用。

### <a name="remarks"></a>备注

有关详细信息，请参阅[并行算法](../../../parallel/concrt/parallel-algorithms.md)。

##  <a name="parallel_for_each"></a>  parallel_for_each

`parallel_for_each` 以并行方式将指定函数应用于某个范围内的每个元素。 除对元素并行执行迭代以及未指定迭代的顺序外，它在语义上等效于 `std` 命名空间中的 `for_each` 函数。 实际自变量 `_Func` 必须支持窗体 `operator()(T)` 的函数调用运算符，其中形式参数 `T` 是正在被循环访问的容器的项类型。

```
template <typename _Iterator, typename _Function>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func);

template <typename _Iterator, typename _Function, typename _Partitioner>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func,
    _Partitioner&& _Part);
```

### <a name="parameters"></a>参数

*_Iterator*<br/>
用于循环访问容器的迭代器的类型。

*_Function*<br/>
将应用于每个元素的范围内的函数的类型。

*_Partitioner*<br/>
*first*<br/>
迭代器，用于寻址第一个元素的位置包括在并行迭代中。

*最后一个*<br/>
发现的迭代器的最后一个元素之后的位置包括在并行迭代中。

*_Func*<br/>
应用于每个元素的范围中一个用户定义函数对象。

*部件 （_p)*<br/>
对分区程序对象的引用。 参数可以是之一`const` [auto_partitioner](auto-partitioner-class.md)`&`， `const` [static_partitioner](static-partitioner-class.md)`&`， `const` [simple_分区程序](simple-partitioner-class.md)`&`或[affinity_partitioner](affinity-partitioner-class.md) `&`如果[affinity_partitioner](affinity-partitioner-class.md)对象，该引用必须是一个非常量左值引用，以便算法可以存储状态，供未来循环重用。

### <a name="remarks"></a>备注

[auto_partitioner](auto-partitioner-class.md)将用于而无需显式分区程序的重载。

有关迭代器不支持随机访问，仅[auto_partitioner](auto-partitioner-class.md)支持。

有关详细信息，请参阅[并行算法](../../../parallel/concrt/parallel-algorithms.md)。

##  <a name="parallel_invoke"></a>  parallel_invoke

执行作为参数并行提供的函数对象，并在它们完成执行后进行阻止。 每个函数对象都可以是 lambda 表达式、函数指针或支持具有签名 `void operator()()` 的函数调用运算符的任何对象。

```
template <typename _Function1, typename _Function2>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2);

template <typename _Function1, typename _Function2, typename _Function3>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9,
    typename _Function10>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9,
    const _Function10& _Func10);
```

### <a name="parameters"></a>参数

*_Function1*<br/>
要并行执行的第一个函数对象的类型。

*_Function2*<br/>
要并行执行的第二个函数对象的类型。

*_Function3*<br/>
要并行执行的第三个函数对象的类型。

*_Function4*<br/>
要并行执行的第四个函数对象的类型。

*_Function5*<br/>
要并行执行的第五个函数对象的类型。

*_Function6*<br/>
要并行执行的第六个函数对象的类型。

*_Function7*<br/>
要并行执行的第七个函数对象的类型。

*_Function8*<br/>
要并行执行的第八个函数对象的类型。

*_Function9*<br/>
要并行执行的第九个函数对象的类型。

*_Function10*<br/>
要并行执行的第十个函数对象的类型。

*_Func1*<br/>
要并行执行的第一个函数对象。

*_Func2*<br/>
要并行执行的第二个函数对象。

*_Func3*<br/>
要并行执行的第三个函数对象。

*_Func4*<br/>
要并行执行的第四个函数对象。

*_Func5*<br/>
要并行执行的第五个函数对象。

*_Func6*<br/>
要并行执行的第六个函数对象。

*_Func7*<br/>
要并行执行的第七个函数对象。

*_Func8*<br/>
要并行执行的第八个函数对象。

*_Func9*<br/>
要并行执行的第九个函数对象。

*_Func10*<br/>
要并行执行的第十个函数对象。

### <a name="remarks"></a>备注

请注意，一个或多个函数对象提供参数可能会将在调用上下文中执行内联。

如果一个或多个函数对象作为参数传递给此函数将引发异常，运行时将选择其选择的一个此类异常，并将其传播到调用`parallel_invoke`。

有关详细信息，请参阅[并行算法](../../../parallel/concrt/parallel-algorithms.md)。

##  <a name="parallel_radixsort"></a>  parallel_radixsort

使用基数排序算法将指定范围中的元素按非降序顺序排列。 这是一个稳定排序函数，它需要可以投影要按无符号整数键排序的元素的投影函数。 默认初始化对于待排序的元素是必须的。

```
template<typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator, typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator, typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);
```

### <a name="parameters"></a>参数

*_Random_iterator*<br/>
输入范围的迭代器类型。

*_Allocator*<br/>
C + + 标准库兼容的内存分配器的类型。

*_Function*<br/>
投影函数的类型。

*（_b)*<br/>
一种随机访问迭代器，用于寻址要排序的范围中第一个元素的位置。

*（_e)*<br/>
一种随机访问迭代器，用于定址要排序的范围中最后元素之后下一个元素的位置。

*_Alloc*<br/>
C + + 标准库兼容的内存分配器的实例。

*_Proj_func*<br/>
将元素转换为整数值用户定义投影函数对象。

*_Chunk_size*<br/>
最小大小的区块将拆分为两个区块用于并行执行。

### <a name="remarks"></a>备注

所有重载都需要`n * sizeof(T)`附加空间，其中`n`是要进行排序的元素数和`T`是元素类型。 具有签名一元投影函子`I _Proj_func(T)`需要返回键在给定元素，其中`T`是元素类型和`I`是无符号的整数类型。

如果未提供的投影函数，只需返回的元素的默认投影函数用于整数类型。 该函数将无法编译如果元素不是整数类型中不存在的投影函数。

如果未提供的分配器类型或实例，c + + 标准库内存分配器`std::allocator<T>`用于分配的缓冲区。

算法将输入范围分为两个区块，然后将每个区块分成两个以并行方式执行的子区块。 可选自变量 `_Chunk_size` 可用于向算法指示它应按顺序处理区块的大小 < `_Chunk_size`。

##  <a name="parallel_reduce"></a>  parallel_reduce

通过计算连续部分和来计算指定范围中所有元素的和，或计算类似的通过指定的二元运算（而不是求和运算）获得的连续部分结果的结果（以并行方式）。 `parallel_reduce` 与 `std::accumulate` 在语义上相似，但它需要二元运算是关联的，并需要标识值（而不是初始值）。

```
template<typename _Forward_iterator>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity);

template<typename _Forward_iterator, typename _Sym_reduce_fun>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity,
    _Sym_reduce_fun _Sym_fun);

template<typename _Reduce_type,
    typename _Forward_iterator,
    typename _Range_reduce_fun,
    typename _Sym_reduce_fun>
inline _Reduce_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const _Reduce_type& _Identity,
    const _Range_reduce_fun& _Range_fun,
    const _Sym_reduce_fun& _Sym_fun);
```

### <a name="parameters"></a>参数

*_Forward_iterator*<br/>
输入范围的迭代器类型。

*_Sym_reduce_fun*<br/>
对称减少函数的类型。 这必须是具有签名的函数类型`_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`，其中 _Reduce_type 是相同的标识类型和减少的结果类型。 用于第三个重载，这应该是一致的输出类型`_Range_reduce_fun`。

*_Reduce_type*<br/>
输入会减少为，可以是不同于输入的元素类型的类型。 返回值和标识值将具有此类型。

*_Range_reduce_fun*<br/>
范围减少函数的类型。 这必须是具有签名的函数类型`_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`，_Reduce_type 是相同的标识类型和减少的结果类型。

*（_b)*<br/>
输入迭代器，用于寻址的范围中的第一个元素会减少。

*（_e)*<br/>
发现要减少的范围内最后一个元素之外的一个位置的元素的输入迭代器。

*_Identity*<br/>
标识值`_Identity`的减少的结果类型与相同的类型以及`value_type`迭代器的第一个和第二个重载。 用于第三个重载，标识值必须与缩短，原本的结果类型相同的类型，但可以不同于`value_type`的迭代器。 它必须具有适当的值，范围 reduction 运算符`_Range_fun`，当应用于一定范围的单个元素的类型`value_type`的标识值的行为类似于类型中的值的类型强制转换和`value_type`为标识类型。

*_Sym_fun*<br/>
将中的第二个减少使用对称函数。 有关详细信息，请参阅备注。

*_Range_fun*<br/>
将在减少的第一阶段中使用的函数。 有关详细信息，请参阅备注。

### <a name="return-value"></a>返回值

减少的结果。

### <a name="remarks"></a>备注

若要执行并行缩减，该函数会将范围分成区块根据基础计划程序可供工作线程的数目。 减少发生在两个阶段、 第一阶段执行每个区块中的减少和第二个阶段执行每个区块的部分结果之间的减少。

第一个重载需要迭代器的`value_type`， `T`，作为标识值类型，以及减少结果类型为相同。 元素类型 T 必须提供该运算符`T T::operator + (T)`以减少每个区块中的元素。 第二个阶段中使用相同的运算符。

第二个重载还需要迭代器的`value_type`是相同的作为标识值类型，以及减少结果类型。 提供的二进制运算符`_Sym_fun`用于这两种降低阶段，使用的标识值与第一阶段的初始值。

用于第三个重载，标识值类型必须相同为减少结果类型，但迭代器的`value_type`可能会从这两个不同。 范围减少函数`_Range_fun`可在使用标识值的第一阶段中作为初始值和二元函数`_Sym_reduce_fun`应用到子在第二个阶段的结果。

##  <a name="parallel_sort"></a>  parallel_sort

将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列（以并行方式）。 此函数是基于比较、不稳定的就地排序，因此它与 `std::sort` 在语义上相似。

```
template<typename _Random_iterator>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,typename _Function>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>参数

*_Random_iterator*<br/>
输入范围的迭代器类型。

*_Function*<br/>
二元比较函子的类型。

*（_b)*<br/>
一种随机访问迭代器，用于寻址要排序的范围中第一个元素的位置。

*（_e)*<br/>
一种随机访问迭代器，用于定址要排序的范围中最后元素之后下一个元素的位置。

*_Func*<br/>
用户定义的谓词函数对象，定义排序中连续元素要满足的比较条件。 二元谓词采用两个参数并在条件满足时返回 **true** ，不满足时返回 **false**。 该比较器函数必须对序列中的元素对进行严格弱排序。

*_Chunk_size*<br/>
最小大小的区块将拆分为两个区块用于并行执行。

### <a name="remarks"></a>备注

第一个重载使用二进制比较运算符`std::less`。

第二个重载使用提供的应具有签名 `bool _Func(T, T)`（其中 `T` 是输入范围中元素的类型）的二进制比较器。

算法将输入范围分为两个区块，然后将每个区块分成两个以并行方式执行的子区块。 可选自变量 `_Chunk_size` 可用于向算法指示它应按顺序处理区块的大小 < `_Chunk_size`。

##  <a name="parallel_transform"></a>  parallel_transform

将指定的函数对象应用于源范围中的每个元素或两个源范围中的一对元素，并将函数对象的返回值复制到目标范围（以并行方式）。 此函数在语义上等效于 `std::transform`。

```
template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const static_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const simple_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    affinity_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator,
    typename _Partitioner>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op,
    _Partitioner&& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op);
```

### <a name="parameters"></a>参数

*_Input_iterator1*<br/>
第一个或唯一输入迭代器的类型。

*_Output_iterator*<br/>
输出迭代器的类型。

*_Unary_operator*<br/>
在输入范围内每个元素上执行的一元函子的类型。

*_Input_iterator2*<br/>
第二个输入迭代器的类型。

*_Binary_operator*<br/>
在两个源范围的元素上成对执行的二元函子的类型。

*_Partitioner*<br/>
*First1*<br/>
一种输入迭代器，用于定址所操作的第一个或唯一的源范围内第一个元素的位置。

*Last1*<br/>
一种输入迭代器，用于定址所操作的第一个或唯一的源范围内最后元素之后下一个元素的位置。

*_Result*<br/>
一种输出迭代器，用于定址目标范围内第一个元素的位置。

*_Unary_op*<br/>
用户定义的应用于源范围内每个元素的一元函数对象。

*部件 （_p)*<br/>
对分区程序对象的引用。 参数可以是之一`const` [auto_partitioner](auto-partitioner-class.md)`&`， `const` [static_partitioner](static-partitioner-class.md)`&`， `const` [simple_分区程序](simple-partitioner-class.md)`&`或[affinity_partitioner](affinity-partitioner-class.md) `&`如果[affinity_partitioner](affinity-partitioner-class.md)对象，该引用必须是一个非常量左值引用，以便算法可以存储状态，供未来循环重用。

*First2*<br/>
一种输入迭代器，用于定址所操作的第二个源范围内第一个元素的位置。

*_Binary_op*<br/>
用户定义的按向前顺序成对应用于两个源范围的二元函数对象。

### <a name="return-value"></a>返回值

一种输出迭代器，用于寻址接收通过函数对象转换的输出元素的目标范围内最后元素之后下一个元素的位置。

### <a name="remarks"></a>备注

[auto_partitioner](auto-partitioner-class.md)将用于无显式分区程序参数的重载。

有关迭代器不支持随机访问，仅[auto_partitioner](auto-partitioner-class.md)支持。

采用自变量 `_Unary_op` 的重载将一元函子应用于输入范围内的每个元素，从而将输入范围转换为输出范围。 `_Unary_op` 必须支持带有签名 `operator()(T)` 的函数调用运算符，签名中的 `T` 是要循环访问的范围的值类型。

采用参数 `_Binary_op` 的重载将二元函子分别应用于第一个输入范围内的一个元素和第二个输入范围内的一个元素，从而将两个输入范围转换为输出范围。 `_Binary_op` 必须支持具有签名 `operator()(T, U)` 的函数调用运算符，签名中的 `T`, `U` 是两个输入迭代器的值类型。

有关详细信息，请参阅[并行算法](../../../parallel/concrt/parallel-algorithms.md)。

##  <a name="receive"></a>  接收

常规接收实现，允许上下文仅等待来自一个源的数据并筛选所接受的值。

```
template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>参数

*T*<br/>
负载类型。

*_Src*<br/>
指针或对从其预期的数据源的引用。

*超时) (_t*<br/>
最长时间该方法应为其数据，以毫秒为单位。

*_Filter_proc*<br/>
确定是否应接受消息的筛选器函数。

### <a name="return-value"></a>返回值

来自源的负载类型的值。

### <a name="remarks"></a>备注

如果将参数`_Timeout`具有常量以外的值`COOPERATIVE_TIMEOUT_INFINITE`，该异常[operation_timed_out](operation-timed-out-class.md)如果指定的时间内过期之前收到一条消息，将引发。 如果你想为零长度超时，则应使用[try_receive](concurrency-namespace-functions.md)函数，而不是调用`receive`且超时为`0`（零），因为它更高效，未引发超时异常。

有关详细信息，请参阅[消息传递函数](../../../parallel/concrt/message-passing-functions.md)。

##  <a name="run_with_cancellation_token"></a>  run_with_cancellation_token

在给定取消标记的上下文中立即同步执行函数对象。

```
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>参数

*_Function*<br/>
将会调用的函数对象的类型。

*_Func*<br/>
将会执行的函数对象。 此对象必须支持具有 void(void) 签名的函数调用运算符。

*_Ct*<br/>
将控制函数对象隐式取消的取消标记。 如果希望避免执行的函数被要取消的父任务组隐式取消，请使用 `cancellation_token::none()`。

### <a name="remarks"></a>备注

取消 `cancellation_token` 时，将触发函数对象中的任何中断点。 如果父任务具有不同的标记或没有标记，则显式标记 `_Ct` 会将此 `_Func` 从父任务取消中隔离出来。

##  <a name="send"></a>  发送

同步发送操作，它会一直等待，直到目标接受或拒绝消息。

```
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>参数

*T*<br/>
负载类型。

*_Trg*<br/>
指针或向其发送数据的目标引用。

*数据 （_d)*<br/>
对要发送的数据的引用。

### <a name="return-value"></a>返回值

**true**接受该消息，如果**false**否则为。

### <a name="remarks"></a>备注

有关详细信息，请参阅[消息传递函数](../../../parallel/concrt/message-passing-functions.md)。

##  <a name="set_ambient_scheduler"></a>  set_ambient_scheduler

```
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>参数

*_Scheduler*<br/>
若要设置环境计划程序。

##  <a name="set_task_execution_resources"></a>  set_task_execution_resources

将并发运行时内部工作线程使用的执行资源限制为指定的关联集。

仅在创建资源管理器之前，或在两个资源管理器生存期之间调用此方法才是有效的。 只要资源管理器在调用时不存在，就可以多次调用它。 设置关联限制后，它仍然有效，直到对 `set_task_execution_resources` 方法的下一次有效调用。

提供的关联掩码不需要是进程关联掩码的子集。 如果需要，将更新过程关联。

```
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>参数

*_ProcessAffinityMask*<br/>
限于并发运行时辅助线程使用的关联掩码。 仅在想要将并发运行时限制为当前处理器组的一部分时，在具有 64 个以上硬件线程的系统上使用此方法。 通常，应使用接受将组关联的数组作为参数的方法版本，以限制具有 64 个以上硬件线程的计算机上的关联。

*count*<br/>
数组中参数 `GROUP_AFFINITY` 指定的 `_PGroupAffinity` 项的数目。

*_PGroupAffinity*<br/>
`GROUP_AFFINITY` 项的数组。

### <a name="remarks"></a>备注

该方法将引发[invalid_operation](invalid-operation-class.md)异常是否存在时调用，资源管理器和一个[invalid_argument](../../../standard-library/invalid-argument-class.md)异常，如果指定的关联产生空集资源。

应仅在具有 Windows 7 或更高版本的操作系统上使用接受组关联作为参数的方法版本。 否则为[invalid_operation](invalid-operation-class.md)引发异常。

调用此方法后以编程方式修改进程关联，将不会导致资源管理器重新计算限于其使用的关联。 因此，对进程关联的所有更改都应在调用此方法之前进行。

##  <a name="swap"></a>  swap

交换两个 `concurrent_vector` 对象的元素。

```
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>参数

*T*<br/>
并发向量中存储的元素数据类型。

*_Ax*<br/>
并发向量的分配器类型。

*_A*<br/>
其元素将要与并发向量的交换的并发向量`_B`。

*_B*<br/>
提供要交换的元素的并发向量或其元素将要与并发向量的交换的向量`_A`。

### <a name="remarks"></a>备注

模板函数是容器类上专用化的算法`concurrent_vector`用以执行成员函数`_A`。 [concurrent_vector:: swap](concurrent-vector-class.md#swap)( `_B`)。 这些是由编译器进行的函数模板部分排序的实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 模板函数的通用版本`template <class T> void swap(T&, T&)`，在算法类按分配工作，是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

此方法不是并发安全的。 您必须确保在调用此方法时，没有其他线程正在执行的并发向量中的任何一个的操作。

##  <a name="task_from_exception"></a>  task_from_exception

```
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>参数

*_TaskType*<br/>

*_ExType*<br/>

*_Exception*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>返回值

##  <a name="task_from_result"></a>  task_from_result

```
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>参数

*T*<br/>

*_Param*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>返回值

##  <a name="trace_agents_register_name"></a>  Trace_agents_register_name

在 ETW 跟踪中将给定名称关联到消息块或代理。

```
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>参数

*T*<br/>
对象的类型。 这通常是消息块或代理。

*_PObject*<br/>
指向在跟踪中命名的消息块或代理的指针。

*名称 （_n)*<br/>
给定对象的名称。

##  <a name="try_receive"></a>  try_receive

常规尝试-接收实现，允许上下文仅查找来自一个源的数据并筛选所接受的值。 如果数据未准备就绪，该方法将返回**false**。

```
template <class T>
bool try_receive(_Inout_ ISource<T>* _Src, T& _value);

template <class T>
bool try_receive(
    _Inout_ ISource<T>* _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);

template <class T>
bool try_receive(ISource<T>& _Src, T& _value);

template <class T>
bool try_receive(
    ISource<T>& _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);
```

### <a name="parameters"></a>参数

*T*<br/>
负载类型

*_Src*<br/>
指针或对从其预期的数据源的引用。

*_value*<br/>
对放置结果的位置的引用。

*_Filter_proc*<br/>
确定是否应接受消息的筛选器函数。

### <a name="return-value"></a>返回值

一个`bool`值，该值指示是否将负载置于中`_value`。

### <a name="remarks"></a>备注

有关详细信息，请参阅[消息传递函数](../../../parallel/concrt/message-passing-functions.md)。

##  <a name="wait"></a>  等待

将当前上下文暂停指定的一段时间。

```
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>参数

*_Milliseconds*<br/>
当前上下文应该暂停的毫秒数。 如果 `_Milliseconds` 参数设置为值 `0`，则当前上下文应在继续之前执行其他可运行的上下文。

### <a name="remarks"></a>备注

如果在并发运行时计划程序上下文调用此方法时，计划程序会发现不同的上下文的基础资源上运行。 由于计划程序在本质上是合作的，此上下文不会正好在指定的毫秒数后继续。 如果计划程序正忙于执行不协作产生计划程序的其他任务，那么等待时间可能是无限期。

##  <a name="when_all"></a>  when_all

创建一个任务，在作为自变量提供的所有任务成功完成后，此任务将成功完成。

```
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) ->
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```

### <a name="parameters"></a>参数

*_Iterator*<br/>
输入迭代器的类型。

*（_b)*<br/>
要合并到结果任务的元素范围中第一个元素的位置。

*（_e)*<br/>
超出要合并到结果任务的元素范围的第一个元素的位置。

*_TaskOptions*<br/>
`task_options` 对象。

### <a name="return-value"></a>返回值

将在所有输入任务成功完成后成功完成的任务。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::vector<T>>`。 如果输入任务的类型为 `void`，则输出任务也将是 `task<void>`。

### <a name="remarks"></a>备注

`when_all` 是生成 `task` 作为其结果的的非阻止函数。 与不同[task:: wait](task-class.md#wait)，则可以安全地在 ASTA (应用程序 STA) 线程上的 UWP 应用中调用此函数。

如果一个任务被取消或引发异常，则返回的任务将提前，完成在取消状态，并且，如果遇到，将引发异常如果调用[task:: get](task-class.md#get)或`task::wait`上该任务。

有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

##  <a name="when_any"></a>  when_any

创建一个任务，在作为自变量提供的任何任务成功完成后，此任务将成功完成。

```
template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options())
    -> decltype (
        details::_WhenAnyImpl<
            typename std::iterator_traits<_Iterator>::value_type::result_type,
            _Iterator>::_Perform(_TaskOptions, _Begin, _End));

template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    cancellation_token _CancellationToken)
       -> decltype (
           details::_WhenAnyImpl<
               typename std::iterator_traits<_Iterator>::value_type::result_type,
               _Iterator>::_Perform(_CancellationToken._GetImplValue(), _Begin, _End));
```

### <a name="parameters"></a>参数

*_Iterator*<br/>
输入迭代器的类型。

*（_b)*<br/>
要合并到结果任务的元素范围中第一个元素的位置。

*（_e)*<br/>
超出要合并到结果任务的元素范围的第一个元素的位置。

*_TaskOptions*<br/>
*_CancellationToken*<br/>
控制返回的任务的取消的取消标记。 如果未提供取消标记，则结果任务将接收到导致任务完成的任务取消标记。

### <a name="return-value"></a>返回值

在任意输入任务成功完成后成功完成的任务。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::pair<T, size_t>>>`，其中的 pair 的第一个元素是正在完成的任务的结果，第二个元素是已完成的任务的索引。 如果输入任务的类型为 `void`，则输出为 `task<size_t>`，其中的结果是正在完成的任务的索引。

### <a name="remarks"></a>备注

`when_any` 是生成 `task` 作为其结果的的非阻止函数。 与不同[task:: wait](task-class.md#wait)，则可以安全地在 ASTA (应用程序 STA) 线程上的 UWP 应用中调用此函数。

有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
