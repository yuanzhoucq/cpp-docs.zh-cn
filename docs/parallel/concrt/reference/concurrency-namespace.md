---
title: "并发 Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_priority_queue/concurrency
- agents/concurrency
- concurrent_vector/concurrency
- concrt/concurrency
- internal_split_ordered_list/concurrency
- concurrent_queue/concurrency
- pplcancellation_token/concurrency
- pplinterface/concurrency
- ppltasks/concurrency
- ppl/concurrency
- concurrent_unordered_map/concurrency
- concrtrm/concurrency
- concurrent_unordered_set/concurrency
- pplconcrt/concurrency
- internal_concurrent_hash/concurrency
dev_langs:
- C++
helpviewer_keywords:
- Concurrency namespace
ms.assetid: f1d33ca2-679b-4442-b140-22a9d9df61d1
caps.latest.revision: 37
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 70c0c5b5897e1cf4aabfefd66ed5f9eef85813c7
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace"></a>concurrency 命名空间
`Concurrency` 命名空间提供可让你访问 C++ 的并发运行和并发编程框架的类和函数。 有关详细信息，请参阅[并发运行时](../../../parallel/concrt/concurrency-runtime.md)。  
  
## <a name="syntax"></a>语法  
  
```  
namespace concurrency;  
```  
  
## <a name="members"></a>成员  
  
### <a name="namespaces"></a>命名空间  
  
|名称|说明|  
|----------|-----------------|  
|[concurrency::extensibility Namespace](http://msdn.microsoft.com/en-us/16a86ff2-128e-4edf-89e4-38aac79c81f9)||  
  
### <a name="typedefs"></a>Typedef  
  
|名称|说明|  
|----------|-----------------|  
|`runtime_object_identity`|每个消息实例都后接一个标识，因为它已被克隆并在消息组件之间传递。 这不能是消息对象的地址。|  
|`task_status`|表示任务的终端状态的类型。 有效值为 `completed` 和 `canceled`。|  
|`TaskProc`|任务的基本抽象，定义为 `void (__cdecl * TaskProc)(void *)`。 调用 `TaskProc` 以调用任务正文。|  
|`TaskProc_t`|任务的基本抽象，定义为 `void (__cdecl * TaskProc_t)(void *)`。 调用 `TaskProc` 以调用任务正文。|  
  
### <a name="classes"></a>类  
  
|名称|说明|  
|----------|-----------------|  
|[affinity_partitioner 类](affinity-partitioner-class.md)|`affinity_partitioner` 类与 `static_partitioner` 类相似，但它选择将子范围映射到工作线程，从而改善缓存关联。 在同一数据集中重新执行循环且数据适应缓存时，它可以显著提高性能。 请注意，必须与在特定数据集中执行的并行循环的后续迭代一起使用同一 `affinity_partitioner` 对象，才能受益于数据位置。|  
|[agent 类](agent-class.md)|旨在用作所有独立代理的基类的类。 用于对其他代理隐藏状态并通过消息传递进行交互。|  
|[auto_partitioner 类](auto-partitioner-class.md)|`auto_partitioner` 类表示 `parallel_for`、`parallel_for_each` 和 `parallel_transform` 用于对其循环访问的范围进行分区的默认方法。 此分区方法使用范围窃取进行负载平衡以及按循环访问取消。|  
|[bad_target 类](bad-target-class.md)|此类描述消息块被给予指向目标的指针，但该目标对于正在执行的操作无效时引发的异常。|  
|[call 类](call-class.md)|`call` 消息块是多源、有序的 `target_block`，可以在接收消息时调用指定函数。|  
|[cancellation_token 类](cancellation-token-class.md)|`cancellation_token` 类表示确定某项操作是否已请求取消的功能。 给定的标记可与 `task_group`、`structured_task_group` 或 `task` 关联以实现隐式取消。 它还可为了取消而进行轮询，或可在取消关联的 `cancellation_token_source` 时注册回调。|  
|[cancellation_token_registration 类](cancellation-token-registration-class.md)|`cancellation_token_registration` 类表示来自 `cancellation_token` 的回调通知。 如果 `register` 上的 `cancellation_token` 方法用于接收何时进行取消的通知，则系统就会将 `cancellation_token_registration` 对象作为回调的句柄返回，以便调用方可以请求特定回调，而不再通过使用 `deregister` 方法来实现。|  
|[cancellation_token_source 类](cancellation-token-source-class.md)|`cancellation_token_source` 类表示取消某个可取消操作的功能。|  
|[choice 类](choice-class.md)|`choice` 消息块是多源、单目标的块，表示与一组源进行的控制流交互。 choice 块将等待多个源中的任何一个源以生成消息，并将传播生成该消息的源的索引。|  
|[combinable 类](combinable-class.md)|`combinable<T>` 对象旨在提供数据的线程专用副本，以在并行算法期间执行无锁线程本地子计算。 在并行操作结束时，线程专用子计算可随之合并到最终结果。 此类可替代共享变量使用，并可能会带来性能提升（如果该共享变量上存在大量争用）。|  
|[concurrent_priority_queue 类](concurrent-priority-queue-class.md)|`concurrent_priority_queue` 类是允许多个线程并发推送和弹出项的容器。 项按优先级顺序弹出，其中优先级由作为模板自变量提供的涵子确定。|  
|[concurrent_queue 类](concurrent-queue-class.md)|`concurrent_queue` 类是允许对其元素进行先进先出访问的序列容器类。 它支持一组有限的并发安全操作，例如 `push` 和 `try_pop`。|  
|[concurrent_unordered_map 类](concurrent-unordered-map-class.md)|`concurrent_unordered_map` 类是控制 `std::pair<const K, _Element_type>` 类型元素的长短不一序列的并发安全容器。 序列以支持并发安全追加、元素访问、迭代器访问和迭代器遍历操作的方式表示。|  
|[concurrent_unordered_multimap 类](concurrent-unordered-multimap-class.md)|`concurrent_unordered_multimap` 类是控制 `std::pair<const K, _Element_type>` 类型元素的长短不一序列的并发安全容器。 序列以支持并发安全追加、元素访问、迭代器访问和迭代器遍历操作的方式表示。|  
|[concurrent_unordered_multiset 类](concurrent-unordered-multiset-class.md)|`concurrent_unordered_multiset`类是并发安全的容器，用于控制的不同长序列的元素类型 k。支持并发安全的方式表示该序列追加、 元素访问、 迭代器访问和迭代器遍历操作。|  
|[concurrent_unordered_set 类](concurrent-unordered-set-class.md)|`concurrent_unordered_set`类是并发安全的容器，用于控制的不同长序列的元素类型 k。支持并发安全的方式表示该序列追加、 元素访问、 迭代器访问和迭代器遍历操作。|  
|[concurrent_vector 类](concurrent-vector-class.md)|`concurrent_vector` 类是允许对任意元素进行随机访问的序列容器类。 它支持并发安全追加、元素访问、迭代器访问和迭代器遍历操作。|  
|[Context 类](context-class.md)|表示执行上下文的抽象。|  
|[context_self_unblock 类](context-self-unblock-class.md)|此类描述从同一上下文调用 `Context` 对象的 `Unblock` 方法时引发的异常。 这将指示给定上下文解除阻止自身的尝试。|  
|[context_unblock_unbalanced 类](context-unblock-unbalanced-class.md)|此类描述对 `Context` 对象的 `Block` 和 `Unblock` 方法的调用未恰当配对时引发的异常。|  
|[critical_section 类](critical-section-class.md)|明确感知并发运行时的不可重入互斥。|  
|[CurrentScheduler 类](currentscheduler-class.md)|表示与调用上下文关联的当前计划程序的抽象。|  
|[default_scheduler_exists 类](default-scheduler-exists-class.md)|此类描述在进程内已存在默认计划程序的情况下调用 `Scheduler::SetDefaultSchedulerPolicy` 方法时引发的异常。|  
|[event 类](event-class.md)|明确感知并发运行时的手动重置事件。|  
|[improper_lock 类](improper-lock-class.md)|此类描述错误获取锁时引发的异常。|  
|[improper_scheduler_attach 类](improper-scheduler-attach-class.md)|此类描述在已附加到当前上下文的 `Scheduler` 对象上调用 `Attach` 方法时引发的异常。|  
|[improper_scheduler_detach 类](improper-scheduler-detach-class.md)|此类描述在尚未附加到任何使用 `Scheduler` 对象的 `Attach` 方法的计划程序的上下文中调用 `CurrentScheduler::Detach` 方法时引发的异常。|  
|[improper_scheduler_reference 类](improper-scheduler-reference-class.md)|此类描述从不属于该计划程序的上下文中，在正在关闭的 `Scheduler` 对象上调用 `Reference` 方法时引发的异常。|  
|[invalid_link_target 类](invalid-link-target-class.md)|此类描述调用消息块的 `link_target` 方法且消息块无法链接到目标时引发的异常。 这可能是因为超出消息块允许的链接数或两次尝试将特定目标链接到同一源。|  
|[invalid_multiple_scheduling 类](invalid-multiple-scheduling-class.md)|此类描述在没有对 `wait` 或 `run_and_wait` 方法进行干预调用的情况下，通过 `task_group` 或 `structured_task_group` 对象的 `run` 方法对 `task_handle` 对象进行多次计划时引发的异常。|  
|[invalid_operation 类](invalid-operation-class.md)|此类描述执行无效操作时引发的异常，由并发运行时引发的其他异常类型不会对此异常进行更为准确的描述。|  
|[invalid_oversubscribe_operation 类](invalid-oversubscribe-operation-class.md)|此类描述在先前没有对 `Context::Oversubscribe` 方法进行调用（`_BeginOversubscription` 参数设置为 `true`）的情况下，调用 `Context::Oversubscribe` 方法（`_BeginOversubscription` 参数设置为 `false`）时引发的异常。|  
|[invalid_scheduler_policy_key 类](invalid-scheduler-policy-key-class.md)|此类描述无效或未知键传递给 `SchedulerPolicy` 对象构造函数，或 `SchedulerPolicy` 对象的 `SetPolicyValue` 方法被传递了必须使用其他方式（例如 `SetConcurrencyLimits` 方法）进行更改的键时引发的异常。|  
|[invalid_scheduler_policy_thread_specification 类](invalid-scheduler-policy-thread-specification-class.md)|此类描述尝试设置 `SchedulerPolicy` 对象的并发限制，以便 `MinConcurrency` 键的值小于 `MaxConcurrency` 键的值时引发的异常。|  
|[invalid_scheduler_policy_value 类](invalid-scheduler-policy-value-class.md)|此类描述 `SchedulerPolicy` 对象的策略键设置为对于该键无效的值时引发的异常。|  
|[ISource 类](isource-class.md)|`ISource` 类是所有源块的接口。 源块将消息传播到 `ITarget` 块。|  
|[ITarget 类](itarget-class.md)|`ITarget` 类是所有目标块的接口。 目标块使用 `ISource` 块提供给它们的消息。|  
|[join 类](join-class.md)|`join` 消息块是单目标、多源、有序的 `propagator_block`，它可以合并来自其每个源的 `T` 类型消息。|  
|[location 类](location-class.md)|硬件上物理位置的抽象。|  
|[message 类](message-class.md)|包含正在消息块之间传递的数据负载的基本消息信封。|  
|[message_not_found 类](message-not-found-class.md)|此类描述消息块找不到请求的消息时引发的异常。|  
|[message_processor 类](message-processor-class.md)|`message_processor` 类是用于处理 `message` 对象的抽象基类。 不能保证消息的排序。|  
|[missing_wait 类](missing-wait-class.md)|此类描述执行对象的析构函数时仍有计划到 `task_group` 或 `structured_task_group` 对象的任务时引发的异常。 如果因为堆栈展开为异常的结果而到达析构函数的调用条件，则永远不会引发此异常。|  
|[multi_link_registry 类](multi-link-registry-class.md)|`multi_link_registry` 对象是管理多个源块或多个目标块的 `network_link_registry`。|  
|[multitype_join 类](multitype-join-class.md)|`multitype_join` 消息块是多源、单目标的消息块，可以合并来自其每个源的不同类型的消息并向其目标提供合并的消息的元组。|  
|[nested_scheduler_missing_detach 类](nested-scheduler-missing-detach-class.md)|此类描述并发运行时检测到你没有在通过 `Scheduler` 对象的 `Attach` 方法附加到第二个计划程序的上下文中调用 `CurrentScheduler::Detach` 方法时引发的异常。|  
|[network_link_registry 类](network-link-registry-class.md)|`network_link_registry` 抽象基类管理源块和目标块之间的链接。|  
|[operation_timed_out 类](operation-timed-out-class.md)|此类描述操作超时时引发的异常。|  
|[ordered_message_processor 类](ordered-message-processor-class.md)|`ordered_message_processor` 是允许消息块按接收顺序处理消息的 `message_processor`。|  
|[overwrite_buffer 类](overwrite-buffer-class.md)|`overwrite_buffer` 消息块是多目标、多源、有序的 `propagator_block`，一次能够存储一条消息。 新消息覆盖之前保存的消息。|  
|[progress_reporter 类](progress-reporter-class.md)|进度报告器类允许报告特定类型的进度通知。 每个 progress_reporter 对象都是绑定到特定异步动作或操作的。|  
|[propagator_block 类](propagator-block-class.md)|`propagator_block` 类是同时为源和目标的消息块的抽象基类。 它合并了 `source_block` 和 `target_block` 类的功能。|  
|[reader_writer_lock 类](reader-writer-lock-class.md)|具有仅限本地旋转的基于编写器首选队列的读取器-编写器锁。 锁授予对编写器的先进先出 (FIFO) 访问权限，并在出现编写器持续负载的情况下停止读取器。|  
|[ScheduleGroup 类](schedulegroup-class.md)|表示计划组的抽象。 计划组整理受益于在时间上（通过在移动到另一个组之前执行同一个组中的另一个任务）或空间上（通过在同一 NUMA 节点或物理套接字上执行同一个组内的多个项）紧密计划在一起的一组相关工作。|  
|[Scheduler 类](scheduler-class.md)|表示并发运行时计划程序的抽象。|  
|[scheduler_not_attached 类](scheduler-not-attached-class.md)|此类描述需要将计划程序附加到当前上下文以执行操作，而实际并未进行附加即执行该操作时引发的异常。|  
|[scheduler_resource_allocation_error 类](scheduler-resource-allocation-error-class.md)|此类描述因未能在并发运行时中获取关键资源而引发的异常。|  
|[scheduler_worker_creation_error 类](scheduler-worker-creation-error-class.md)|此类描述因未能在并发运行时中创建辅助执行上下文而引发的异常。|  
|[SchedulerPolicy 类](schedulerpolicy-class.md)|`SchedulerPolicy` 类包含一组控制计划程序实例的行为的键/值对，一个键/值对对应于一个策略元素。|  
|[simple_partitioner 类](simple-partitioner-class.md)|`simple_partitioner` 类表示由 `parallel_for` 循环访问的范围的静态分区。 分区程序将该范围分成区块，以便每个区块都至少具有区块大小指定的迭代数量。|  
|[single_assignment 类](single-assignment-class.md)|`single_assignment` 消息块是多目标、多源、有序的 `propagator_block`，能够存储单个一次写入的 `message`。|  
|[single_link_registry 类](single-link-registry-class.md)|`single_link_registry` 对象是仅管理单个源块或目标块的 `network_link_registry`。|  
|[source_block 类](source-block-class.md)|`source_block` 是仅限于源的块的抽象基类。 该类提供基本链接管理功能和常见错误检查。|  
|[source_link_manager 类](source-link-manager-class.md)|`source_link_manager` 对象管理到 `ISource` 块的消息块网络链接。|  
|[static_partitioner 类](static-partitioner-class.md)|`static_partitioner` 类表示由 `parallel_for` 循环访问的范围的静态分区。 只要基础计划程序有工作线程可用，分区程序就会将范围分成尽可能多的区块。|  
|[structured_task_group 类](structured-task-group-class.md)|`structured_task_group` 类表示并行工作的高度结构化集合。 可以使用 `task_handle` 对象将各个并行任务排队到 `structured_task_group` 并等待它们完成，或在它们完成执行之前取消任务组，这将中止尚未开始执行的所有任务。|  
|[target_block 类](target-block-class.md)|`target_block` 类是抽象基类，它提供基本链接管理功能和针对仅限于目标的块的错误检查。|  
|[task 类 （并发运行时）](task-class.md)|并行模式库 (PPL) `task` 类。 `task` 对象，表示可异步执行的工作，以及可与并发运行时中的并行算法生成的其他任务一起执行的工作。 成功完成后，它将生成类型为 `_ResultType` 的结果。 类型为 `task<void>` 的任务不生成任何结果。 可独立于其他任务等待和取消的任务。 它也可通过使用 continuations(`then`)、join(`when_all`) 和 choice(`when_any`) 模式由其他任务构成。|  
|[task_canceled 类](task-canceled-class.md)|此类描述了 PPL 任务层为了强制取消当前任务而引发的异常。 它也会通过引发`get()`方法[任务](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f)，为已取消的任务。|  
|[task_completion_event 类](task-completion-event-class.md)|`task_completion_event` 类可让你延迟任务的执行，直到满足条件，或开始一项任务来响应外部事件。|  
|[task_continuation_context 类](task-continuation-context-class.md)|`task_continuation_context` 类可让你指定想要执行延续的位置。 只能从 Windows 应用商店应用使用此类。 对于非 Windows 应用商店应用，任务延续的执行上下文由运行时确定，不可配置。|  
|[task_group 类](task-group-class.md)|`task_group` 类表示可以等待或取消的并行工作的集合。|  
|[task_handle 类](task-handle-class.md)|`task_handle` 类表示单个并行工作项。 它封装执行一项工作所需的指令和数据。|  
|[task_options 类 （并发运行时）](task-options-class-concurrency-runtime.md)|表示可用于创建任务的选项|  
|[timer 类](timer-class.md)|`timer` 消息块是单目标的 `source_block`，能够在经过指定的时间段后或在特定时间间隔向其目标发送消息。|  
|[transformer 类](transformer-class.md)|`transformer` 消息块是单目标、多源、有序的 `propagator_block`，它可以接受一个类型的消息，并能够存储不限数量的另一个类型的消息。|  
|[unbounded_buffer 类](unbounded-buffer-class.md)|`unbounded_buffer` 消息块是多目标、多源、有序的 `propagator_block`，能够存储不限数量的消息。|  
|[unsupported_os 类](unsupported-os-class.md)|此类描述使用不受支持的操作系统时引发的一种异常。|  
  
### <a name="structures"></a>结构  
  
|名称|说明|  
|----------|-----------------|  
|[DispatchState 结构](dispatchstate-structure.md)|`DispatchState` 结构用于将状态传输给 `IExecutionContext::Dispatch` 方法。 它描述了在 `IExecutionContext` 接口上调用 `Dispatch` 方法的情形。|  
|[IExecutionContext 结构](iexecutioncontext-structure.md)|可以在给定虚拟处理器上运行并可以协作切换上下文的执行上下文的接口。|  
|[IExecutionResource 结构](iexecutionresource-structure.md)|硬件线程的抽象。|  
|[IResourceManager 结构](iresourcemanager-structure.md)|并发运行时的资源管理器的接口。 这是计划程序与资源管理器进行通信的接口。|  
|[IScheduler 结构](ischeduler-structure.md)|工作计划程序的抽象的接口。 并发运行时的资源管理器使用此接口与工作计划程序进行通信。|  
|[ISchedulerProxy 结构](ischedulerproxy-structure.md)|计划程序用来与并发运行时的资源管理器进行通信以协商资源分配的接口。|  
|[IThreadProxy 结构](ithreadproxy-structure.md)|执行线程的抽象。 根据你创建的计划程序的 `SchedulerType` 策略键，资源管理器将授予你由普通的 Win32 线程或用户模式计划 (UMS) 线程支持的线程代理。 UMS 线程在具有 Windows 7 或更高版本的 64 位操作系统上受到支持。|  
|[ITopologyExecutionResource 结构](itopologyexecutionresource-structure.md)|资源管理器定义的执行资源的接口。|  
|[ITopologyNode 结构](itopologynode-structure.md)|资源管理器定义的拓扑节点的接口。 一个节点包含一个或多个执行资源。|  
|[IUMSCompletionList 结构](iumscompletionlist-structure.md)|表示 UMS 完成列表。 UMS 线程阻止时，将分派计划程序的指定计划上下文，以便决定原始线程被阻止时，在基础虚拟处理器根上计划哪些内容。 如果原始线程解除阻止，则操作系统将它排队到完成列表，该列表可以通过此接口访问。 计划程序可以在指定计划上下文中或其搜索工作的任何其他位置查询完成列表。|  
|[IUMSScheduler 结构](iumsscheduler-structure.md)|工作计划程序的抽象的接口，该工作计划程序希望并发运行时的资源管理器向其传递用户模式计划 (UMS) 线程。 资源管理器使用此接口与 UMS 线程计划程序进行通信。 `IUMSScheduler` 接口继承自 `IScheduler` 接口。|  
|[IUMSThreadProxy 结构](iumsthreadproxy-structure.md)|执行线程的抽象。 如果想要计划程序获得用户模式计划 (UMS) 线程，则将计划程序策略元素 `SchedulerKind` 的值设置为 `UmsThreadDefault`，并实现 `IUMSScheduler` 接口。 UMS 线程仅在具有 Windows 7 或更高版本的 64 位操作系统上受到支持。|  
|[IUMSUnblockNotification 结构](iumsunblocknotification-structure.md)|表示来自资源管理器的通知，说明阻止并触发返回到计划程序的指定计划上下文的线程代理已解除阻止，并已准备好进行计划。 一旦重新计划该线程代理的关联执行上下文（从 `GetContext` 方法返回），此接口将变得无效。|  
|[IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)|线程代理可在其中执行的硬件线程的抽象。|  
|[scheduler_interface 结构](scheduler-interface-structure.md)|计划程序接口|  
|[scheduler_ptr 结构 （并发运行时）](scheduler-ptr-structure-concurrency-runtime.md)|表示指向计划程序的指针。 此类可用于通过使用 shared_ptr 来允许指定共享生存期，或通过使用原始指针来允许指定无格式引用。|  
  
### <a name="enumerations"></a>枚举  
  
|名称|描述|  
|----------|-----------------|  
|[agent_status 枚举](concurrency-namespace-enums.md#agent_status)|`agent` 的有效状态。|  
|[Agents_EventType 枚举](concurrency-namespace-enums.md#agents_eventtype)|可以使用代理库提供的跟踪功能进行跟踪的事件的类型|  
|[ConcRT_EventType 枚举](concurrency-namespace-enums.md#concrt_eventtype)|可以使用并发运行时提供的跟踪功能进行跟踪的事件的类型。|  
|[Concrt_TraceFlags 枚举](concurrency-namespace-enums.md#concrt_traceflags)|事件类型的跟踪标志|  
|[CriticalRegionType 枚举](concurrency-namespace-enums.md#criticalregiontype)|上下文位于其中的关键区域的类型。|  
|[DynamicProgressFeedbackType 枚举](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|由 `DynamicProgressFeedback` 策略用于描述重新平衡计划程序资源的依据是从计划程序收集的统计信息，还是通过对 `IVirtualProcessorRoot` 接口上的 `Activate` 和 `Deactivate` 方法进行调用以进出空闲状态的虚拟处理器。 有关可用的计划程序策略的详细信息，请参阅[PolicyElementKey 枚举](concurrency-namespace-enums.md#policyelementkey)。|  
|[join_type 枚举](concurrency-namespace-enums.md#join_type)|`join` 消息块的类型。|  
|[message_status 枚举](concurrency-namespace-enums.md#message_status)|`message` 对象的内容到块的有效响应。|  
|[PolicyElementKey 枚举](concurrency-namespace-enums.md#policyelementkey)|描述计划程序行为各个方面的策略键。 每个策略元素由一个键值对描述。 有关计划程序策略和它们的影响计划程序的详细信息，请参阅[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。|  
|[SchedulerType 枚举](concurrency-namespace-enums.md#schedulertype)|由 `SchedulerKind` 策略用于描述应由计划程序用于基础执行上下文的线程的类型。 有关可用的计划程序策略的详细信息，请参阅[PolicyElementKey 枚举](concurrency-namespace-enums.md#policyelementkey)。|  
|[SchedulingProtocolType 枚举](concurrency-namespace-enums.md#schedulingprotocoltype)|由 `SchedulingProtocol` 策略用于描述将哪个计划算法用于计划程序。 有关可用的计划程序策略的详细信息，请参阅[PolicyElementKey 枚举](concurrency-namespace-enums.md#policyelementkey)。|  
|[SwitchingProxyState 枚举](concurrency-namespace-enums.md#switchingproxystate)|用于表示线程代理在执行另一个线程代理的协作上下文切换时所处的状态。|  
|[task_group_status 枚举](concurrency-namespace-enums.md#task_group_status)|描述 `task_group` 或 `structured_task_group` 对象的执行状态。 此类型的值是由很多等待安排到一个任务组中的任务完成的方法返回的。|  
|[WinRTInitializationType 枚举](concurrency-namespace-enums.md#winrtinitializationtype)|由 `WinRTInitialization` 策略用于描述，对于在 Windows 8 或更高版本的操作系统上运行的应用程序，是否以及如何在计划程序的线程上初始化 Windows 运行时。 有关可用的计划程序策略的详细信息，请参阅[PolicyElementKey 枚举](concurrency-namespace-enums.md#policyelementkey)。|  
  
### <a name="functions"></a>函数  
  
|名称|说明|  
|----------|-----------------|  
|[Alloc 函数](concurrency-namespace-functions.md#alloc)|通过并发运行时缓存子分配器分配具有指定大小的内存块。|  
|[asend 函数](concurrency-namespace-functions.md#asend)|已重载。 异步发送操作，计划任务以将数据传播到目标块。|  
|[cancel_current_task 函数](concurrency-namespace-functions.md#cancel_current_task)|获取当前执行的任务。 此函数可从任务主体中进行调用，以便中止任务的执行并使其进入 `canceled` 状态。<br /><br /> 不支持从 `task` 主体外部调用此函数的情况。 这样做将导致未定义的行为，例如应用程序崩溃或挂起。|  
|[create_async 函数](concurrency-namespace-functions.md#create_async)|基于用户提供的 lambda 或函数对象创建 Windows 运行时异步构造。 `create_async` 的返回类型是基于传递给方法的 lambda 的签名的 `IAsyncAction^`、`IAsyncActionWithProgress<TProgress>^`、`IAsyncOperation<TResult>^` 或 `IAsyncOperationWithProgress<TResult, TProgress>^` 之一。|  
|[create_task 函数](concurrency-namespace-functions.md#create_task)|已重载。 创建 PPL[任务](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f)对象。 在你会使用任务构造函数的任何位置都可以使用 `create_task`。 出于便利性提供该函数，因为它允许在创建任务时使用 `auto` 关键字。|  
|[CreateResourceManager 函数](concurrency-namespace-functions.md#createresourcemanager)|返回表示并发运行时的资源管理器的单一实例的接口。 资源管理器负责将资源分配给想要相互合作的计划程序。|  
|[DisableTracing 函数](concurrency-namespace-functions.md#disabletracing)|在并发运行时中禁用跟踪。 此函数被弃用，因为默认注销 ETW 跟踪。|  
|[EnableTracing 函数](concurrency-namespace-functions.md#enabletracing)|在并发运行时中启用跟踪。 此函数被弃用，因为现在默认启用 ETW 跟踪。|  
|[Free 函数](concurrency-namespace-functions.md#free)|释放先前通过 `Alloc` 方法分配给并发运行时的缓存子分配器的内存块。|  
|[get_ambient_scheduler 函数 （并发运行时）](concurrency-namespace-functions.md#get_ambient_scheduler)||  
|[GetExecutionContextId 函数](concurrency-namespace-functions.md#getexecutioncontextid)|返回可以分配给实现 `IExecutionContext` 接口的执行上下文的唯一标识符。|  
|[GetOSVersion 函数](concurrency-namespace-functions.md#getosversion)|返回操作系统版本。|  
|[GetProcessorCount 函数](concurrency-namespace-functions.md#getprocessorcount)|返回基础系统上的硬件线程数。|  
|[GetProcessorNodeCount 函数](concurrency-namespace-functions.md#getprocessornodecount)|返回基础系统上的 NUMA 节点数或处理器包数。|  
|[GetSchedulerId 函数](concurrency-namespace-functions.md#getschedulerid)|返回可以分配给实现 `IScheduler` 接口的计划程序的唯一标识符。|  
|[interruption_point 函数](concurrency-namespace-functions.md#interruption_point)|创建取消的中断点。 如果正在调用此函数的上下文中执行取消操作，则此函数将引发内部异常，该内部异常中止当前执行并行工作的执行。 如果没有正在执行取消操作，则函数不执行任何操作。|  
|[is_current_task_group_canceling 函数](concurrency-namespace-functions.md#is_current_task_group_canceling)|返回在当前上下文中进行内联执行的任务组是否正处于活动取消的过程中（或不久将取消）的指示。 请注意，如果当前上下文中没有当前正在进行内联执行的任务组，则将返回 `false`。|  
|[make_choice 函数](concurrency-namespace-functions.md#make_choice)|已重载。 从可选的 `choice` 或 `Scheduler` 及两个或更多输入源构造 `ScheduleGroup` 消息块。|  
|[make_greedy_join 函数](concurrency-namespace-functions.md#make_greedy_join)|已重载。 从可选的 `greedy multitype_join` 或 `Scheduler` 及两个或更多输入源构造 `ScheduleGroup` 消息块。|  
|[make_join 函数](concurrency-namespace-functions.md#make_join)|已重载。 从可选的 `non_greedy multitype_join` 或 `Scheduler` 及两个或更多输入源构造 `ScheduleGroup` 消息块。|  
|[make_task 函数](concurrency-namespace-functions.md#make_task)|用于创建 `task_handle` 对象的工厂方法。|  
|[parallel_buffered_sort 函数](concurrency-namespace-functions.md#parallel_buffered_sort)|已重载。 将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列（以并行方式）。 此函数是基于比较、不稳定的就地排序，因此它与 `std::sort` 在语义上相似，但它需要 `O(n)` 附加空间，并需要待排序的元素进行默认初始化。|  
|[parallel_for 函数](concurrency-namespace-functions.md#parallel_for)|已重载。 `parallel_for` 循环访问某个索引范围，并在每次迭代时以并行方式执行用户提供的函数。|  
|[parallel_for_each 函数](concurrency-namespace-functions.md#parallel_for_each)|已重载。 `parallel_for_each` 以并行方式将指定函数应用于某个范围内的每个元素。 除对元素并行执行迭代以及未指定迭代的顺序外，它在语义上等效于 `std` 命名空间中的 `for_each` 函数。 实际参数 `_Func` 必须支持窗体 `operator()(T)` 的函数调用运算符，其中形式参数 `T` 是正在被循环访问的容器的项类型。|  
|[parallel_invoke 函数](concurrency-namespace-functions.md#parallel_invoke)|已重载。 执行作为参数并行提供的函数对象，并在它们完成执行后进行阻止。 每个函数对象都可以是 lambda 表达式、函数指针或支持具有签名 `void operator()()` 的函数调用运算符的任何对象。|  
|[parallel_radixsort 函数](concurrency-namespace-functions.md#parallel_radixsort)|已重载。 使用基数排序算法将指定范围中的元素按非降序顺序排列。 这是一个稳定排序函数，它需要可以投影要按无符号整数键排序的元素的投影函数。 默认初始化对于待排序的元素是必须的。|  
|[parallel_reduce 函数](concurrency-namespace-functions.md#parallel_reduce)|已重载。 通过计算连续部分和来计算指定范围中所有元素的和，或计算类似的通过指定的二元运算（而不是求和运算）获得的连续部分结果的结果（以并行方式）。 `parallel_reduce` 与 `std::accumulate` 在语义上相似，但它需要二元运算是关联的，并需要标识值（而不是初始值）。|  
|[parallel_sort 函数](concurrency-namespace-functions.md#parallel_sort)|已重载。 将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列（以并行方式）。 此函数是基于比较、不稳定的就地排序，因此它与 `std::sort` 在语义上相似。|  
|[parallel_transform 函数](concurrency-namespace-functions.md#parallel_transform)|已重载。 将指定的函数对象应用于源范围中的每个元素或两个源范围中的一对元素，并将函数对象的返回值复制到目标范围（以并行方式）。 此函数在语义上等效于 `std::transform`。|  
|[receive 函数](concurrency-namespace-functions.md#receive)|已重载。 常规接收实现，允许上下文仅等待来自一个源的数据并筛选所接受的值。|  
|[run_with_cancellation_token 函数](concurrency-namespace-functions.md#run_with_cancellation_token)|在给定取消标记的上下文中立即同步执行函数对象。|  
|[send 函数](concurrency-namespace-functions.md#send)|已重载。 同步发送操作，它会一直等待，直到目标接受或拒绝消息。|  
|[set_ambient_scheduler 函数 （并发运行时）](concurrency-namespace-functions.md#set_ambient_scheduler)||  
|[set_task_execution_resources 函数](concurrency-namespace-functions.md#set_task_execution_resources)|已重载。 将并发运行时内部工作线程使用的执行资源限制为指定的关联集。<br /><br /> 仅在创建资源管理器之前，或在两个资源管理器生存期之间调用此方法才是有效的。 只要资源管理器在调用时不存在，就可以多次调用它。 设置关联限制后，它仍然有效，直到对 `set_task_execution_resources` 方法的下一次有效调用。<br /><br /> 提供的关联掩码不需要是进程关联掩码的子集。 如果需要，将更新过程关联。|  
|[swap 函数](concurrency-namespace-functions.md#swap)|交换两个 `concurrent_vector` 对象的元素。|  
|[task_from_exception 函数 （并发运行时）](concurrency-namespace-functions.md#task_from_exception)||  
|[task_from_result 函数 （并发运行时）](concurrency-namespace-functions.md#task_from_result)||  
|[Trace_agents_register_name 函数](concurrency-namespace-functions.md#trace_agents_register_name)|在 ETW 跟踪中将给定名称关联到消息块或代理。|  
|[try_receive 函数](concurrency-namespace-functions.md#try_receive)|已重载。 常规尝试-接收实现，允许上下文仅查找来自一个源的数据并筛选所接受的值。 如果数据未就绪，则方法将返回 false。|  
|[wait 函数](concurrency-namespace-functions.md#wait)|将当前上下文暂停指定的一段时间。|  
|[when_all 函数](concurrency-namespace-functions.md#when_all)|创建一个任务，在作为自变量提供的所有任务成功完成后，此任务将成功完成。|  
|[when_any 函数](concurrency-namespace-functions.md#when_any)|已重载。 创建一个任务，在作为参数提供的任何任务成功完成后，此任务将成功完成。|  
  
### <a name="operators"></a>运算符  
  
|名称|说明|  
|----------|-----------------| 
|[运算符 ！ = 运算符](concurrency-namespace-operators.md#operator_neq)|测试运算符左侧的 `concurrent_vector` 对象是否不等于右侧的 `concurrent_vector` 对象。|  
|[运算符 && 运算符](concurrency-namespace-operators.md#operator_amp_amp)|已重载。 创建一个任务，在作为自变量提供的两个任务成功完成后，此任务将成功完成。|  
|[运算符 | |运算符](concurrency-namespace-operators.md#operator_lor)|已重载。 创建将在作为自变量提供的任一任务成功完成时成功完成的任务。|  
|[运算符<>](concurrency-namespace-operators.md#operator_lt)|测试运算符左侧的 `concurrent_vector` 对象是否小于右侧的 `concurrent_vector` 对象。|  
|[运算符<=></=>](concurrency-namespace-operators.md#operator_lt_eq)|测试运算符左侧的 `concurrent_vector` 对象是否小于或等于右侧的 `concurrent_vector` 对象。|  
|[运算符 = = 运算符](concurrency-namespace-operators.md#operator_eq_eq)|测试运算符左侧的 `concurrent_vector` 对象是否等于右侧的 `concurrent_vector` 对象。|  
|[运算符&1;> 运算符](concurrency-namespace-operators.md#operator_gt)|测试运算符左侧的 `concurrent_vector` 对象是否大于右侧的 `concurrent_vector` 对象。|  
|[运算符&1;> = 运算符](concurrency-namespace-operators.md#operator_lt_eq)|测试运算符左侧的 `concurrent_vector` 对象是否大于或等于右侧的 `concurrent_vector` 对象。|  
  
### <a name="constants"></a>常量  
  
|名称|说明|  
|----------|-----------------|  
|[AgentEventGuid 常量](concurrency-namespace-constants1.md#agenteventguid)|类别 GUID ({B9B5B78C-0713-4898-A21A-C67949DCED07})，描述并发运行时中由代理库激发的 ETW 事件。|  
|[ChoreEventGuid 常量](concurrency-namespace-constants1.md#choreeventguid)|类别 GUID，描述由与日常任务或任务直接相关的并发运行时激发的 ETW 事件。|  
|[ConcRT_ProviderGuid 常量](concurrency-namespace-constants1.md#concrt_providerguid)|并发运行时的 ETW 提供程序 GUID。|  
|[CONCRT_RM_VERSION_1 常量](concurrency-namespace-constants1.md#concrt_rm_version_1)|指示支持 Visual Studio 2010 中定义的资源管理器接口。|  
|[ConcRTEventGuid 常量](concurrency-namespace-constants1.md#concrteventguid)|类别 GUID，描述由并发运行时激发的且没有被另一个类别进行更具体描述的 ETW 事件。|  
|[ContextEventGuid 常量](concurrency-namespace-constants1.md#contexteventguid)|类别 GUID，描述由与上下文直接相关的并发运行时激发的 ETW 事件。|  
|[COOPERATIVE_TIMEOUT_INFINITE 常量](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|指示等待永远不应超时的值。|  
|[COOPERATIVE_WAIT_TIMEOUT 常量](concurrency-namespace-constants1.md#cooperative_wait_timeout)|指示等待超时的值。|  
|[INHERIT_THREAD_PRIORITY 常量](concurrency-namespace-constants1.md#inherit_thread_priority)|策略键 `ContextPriority` 的特殊值，指示计划程序中所有上下文的线程优先级都应与创建该计划程序的线程的优先级相同。|  
|[LockEventGuid 常量](concurrency-namespace-constants1.md#lockeventguid)|类别 GUID，描述由与锁直接相关的并发运行时激发的 ETW 事件。|  
|[MaxExecutionResources 常量](concurrency-namespace-constants1.md#maxexecutionresources)|策略键 `MinConcurrency` 和 `MaxConcurrency` 的特殊值。 默认值为没有其他约束的计算机上的硬件线程数。|  
|[PPLParallelForeachEventGuid 常量](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|类别 GUID，描述由与 `parallel_for_each` 函数的用法直接相关的并发运行时激发的 ETW 事件。|  
|[PPLParallelForEventGuid 常量](concurrency-namespace-constants1.md#pplparallelforeventguid)|类别 GUID，描述由与 `parallel_for` 函数的用法直接相关的并发运行时激发的 ETW 事件。|  
|[PPLParallelInvokeEventGuid 常量](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|类别 GUID，描述由与 `parallel_invoke` 函数的用法直接相关的并发运行时激发的 ETW 事件。|  
|[ResourceManagerEventGuid 常量](concurrency-namespace-constants1.md#resourcemanagereventguid)|类别 GUID，描述由与资源管理器直接相关的并发运行时激发的 ETW 事件。|  
|[ScheduleGroupEventGuid 常量](concurrency-namespace-constants1.md#schedulegroupeventguid)|类别 GUID，描述由与计划组直接相关的并发运行时激发的 ETW 事件。|  
|[SchedulerEventGuid 常量](concurrency-namespace-constants1.md#schedulereventguid)|类别 GUID，描述由与计划程序活动直接相关的并发运行时激发的 ETW 事件。|  
|[VirtualProcessorEventGuid 常量](concurrency-namespace-constants1.md#virtualprocessoreventguid)|类别 GUID，描述由与虚拟处理器直接相关的并发运行时激发的 ETW 事件。|  
  
## <a name="requirements"></a>要求  
 **标头︰** agents.h、 concrt.h，concrtrm.h、 concurrent_priority_queue.h、 concurrent_queue.h、 concurrent_unordered_map.h、 concurrent_unordered_set.h、 concurrent_vector.h、 internal_concurrent_hash.h、 internal_split_ordered_list.h、 ppl.h、 pplcancellation_token.h、 pplconcrt.h、 pplinterface.h、 ppltasks.h  
  
## <a name="see-also"></a>另请参阅  
 [参考](reference-concurrency-runtime.md)


