---
title: PPL 中的取消操作
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
ms.openlocfilehash: 6e23ccd6fcae03bcad40ea560356f4d1290dbcdd
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427487"
---
# <a name="cancellation-in-the-ppl"></a>PPL 中的取消操作

本文档说明并行模式库 (PPL) 中取消操作的角色、如何取消并行工作以及如何确定取消并行工作的时间。

> [!NOTE]
> 运行时使用异常处理实现取消操作。 请勿在代码中捕捉或处理这些异常。 此外，还建议你在任务的函数体中编写异常安全的代码。 例如，你可以使用*资源采集为初始化*（RAII）模式，以确保在任务正文中引发异常时正确处理资源。 有关使用 RAII 模式清除可取消任务中的资源的完整示例，请参阅[演练：从用户界面线程中删除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)。

## <a name="key-points"></a>要点

- 取消是协作性的并且涉及在请求取消的代码和响应取消的任务之间的协作。

- 如有可能，使用取消标记取消工作。 [Concurrency：： cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)类定义取消标记。

- 使用取消标记时，请使用[concurrency：： cancellation_token_source：： cancel](reference/cancellation-token-source-class.md#cancel)方法来启动取消，使用[concurrency：： cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task)函数来响应取消。 使用[concurrency：： cancellation_token：： is_canceled](reference/cancellation-token-class.md#is_canceled)方法检查是否有其他任务请求取消。

- 取消不会立即发生。 尽管在取消任务或任务组时未启动新工作，但活动工作必须检查并响应取消。

- 基于值的延续继承前面的任务的取消标记。 基于任务的继续不会继承其前面的任务的标记。

- 如果调用的构造函数或函数采用 `cancellation_token` 对象，但你不希望可取消该操作，请使用[concurrency：： cancellation_token：： none](reference/cancellation-token-class.md#none)方法。 此外，如果未将取消标记传递给[concurrency：： task](../../parallel/concrt/reference/task-class.md)构造函数或[concurrency：： create_task](reference/concurrency-namespace-functions.md#create_task)函数，则该任务不可取消。

## <a name="top"></a>本文档中

- [并行工作树](#trees)

- [取消并行任务](#tasks)

    - [使用取消标记来取消并行工作](#tokens)

    - [使用 cancel 方法取消并行工作](#cancel)

    - [使用异常来取消并行工作](#exceptions)

- [取消并行算法](#algorithms)

- [何时不使用取消](#when)

## <a name="trees"></a>并行工作树

PPL 使用任务和任务组来管理细化的任务和计算。 可以嵌套任务组来形成并行工作*树*。 下图演示了并行工作树。 在该图中，`tg1` 和 `tg2` 表示任务组；`t1`、`t2`、`t3`、`t4` 和 `t5` 表示任务组执行的工作。

![并行工作树](../../parallel/concrt/media/parallelwork_trees.png "并行工作树")

下面的示例演示了创建该图中的树所需的代码。 在此示例中，`tg1` 和 `tg2` 为[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象;`t1`、`t2`、`t3`、`t4`和 `t5` 为[concurrency：： task_handle](../../parallel/concrt/reference/task-handle-class.md)对象。

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

你还可以使用[concurrency：： task_group](reference/task-group-class.md)类创建类似的工作树。 [Concurrency：： task](../../parallel/concrt/reference/task-class.md)类还支持工作树的概念。 但是，`task` 树是依赖关系树。 在 `task` 树中，将来的工作在当前工作之后完成。 在任务组树中，内部工作在外部工作之前完成。 有关任务和任务组之间的差异的详细信息，请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

[[返回页首](#top)]

## <a name="tasks"></a>取消并行任务

可以通过多种方法来取消并行工作。 首选方法是使用取消标记。 任务组还支持[concurrency：： task_group：： cancel](reference/task-group-class.md#cancel)方法和[concurrency：： structured_task_group：： cancel](reference/structured-task-group-class.md#cancel)方法。 最后一种方法是在任务工作函数体中引发异常。 无论选择哪种方法，都应知道取消不会立即发生。 尽管在取消任务或任务组时未启动新工作，但活动工作必须检查并响应取消。

有关取消并行任务的更多示例，请参阅[演练：使用任务和 XML HTTP 请求进行连接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)，[如何：使用取消中断并行循环](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)，[如何：使用异常处理中断并行循环](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。

### <a name="tokens"></a>使用取消标记来取消并行工作

`task`、`task_group` 和 `structured_task_group` 类支持通过使用取消标记进行取消。 PPL 定义[concurrency：： cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)和[concurrency：： cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)类以实现此目的。 当使用取消标记来取消工作时，运行时不会启动订阅此标记的新工作。 已处于活动状态的工作可以使用[is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled)成员函数监视取消标记并在可能时停止。

若要启动取消，请调用[concurrency：： cancellation_token_source：： cancel](reference/cancellation-token-source-class.md#cancel)方法。 可以采用以下方法响应取消：

- 对于 `task` 对象，请使用[concurrency：： cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task)函数。 `cancel_current_task` 取消当前任务及其任何基于值的延续。 （它不会取消与任务或其延续关联的取消*标记*。）

- 对于任务组和并行算法，使用[concurrency：： is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling)函数来检测取消，并在此函数返回**true**时，尽快从任务正文返回。 （请勿从任务组调用 `cancel_current_task`。）

下面的示例演示用于进行任务取消的第一个基本模式。 任务正文偶尔检查循环内的取消。

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

`cancel_current_task` 函数引发；因此，你不必从当前循环或函数显示返回。

> [!TIP]
> 或者，你可以调用[concurrency：： interruption_point](reference/concurrency-namespace-functions.md#interruption_point)函数，而不是 `cancel_current_task`。

响应取消时，请务必调用 `cancel_current_task`，因为任务转换为已取消状态。 如果提前返回而不是调用 `cancel_current_task`，则操作转换为已完成状态并且所有基于值的延续都会运行。

> [!CAUTION]
> 切勿从代码中引发 `task_canceled`。 请改为调用 `cancel_current_task`。

当任务以 "已取消" 状态结束时， [concurrency：： task：： get](reference/task-class.md#get)方法会引发[concurrency：： task_canceled](../../parallel/concrt/reference/task-canceled-class.md)。 （相反， [concurrency：： task：： wait](reference/task-class.md#wait)返回[task_status：：已取消](reference/concurrency-namespace-enums.md#task_group_status)且不引发。）下面的示例演示了基于任务的延续的此行为。 始终调用基于任务的延续，即使前面的任务已取消。

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

由于基于值延续的继承其前面的任务的标记，因此除非它们是使用显式标记创建的，即使前面的任务仍正在执行，延续也会立即进入已取消状态。 因此，在取消后由前面的任务引发的任何异常都不会传播到延续任务。 取消始终替代前面的任务的状态。 下面的示例与前面的示例类似，但说明了基于值的延续的行为。

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> 如果未将取消标记传递给 `task` 构造函数或[concurrency：： create_task](reference/concurrency-namespace-functions.md#create_task)函数，则该任务不可取消。 此外，还必须将相同的取消标记传递给任何嵌套的任务（即，在另一项任务的正文中创建的任务）的构造函数，以同时取消所有任务。

你可能想要在取消标记被取消时运行任意代码。 例如，如果用户在用户界面上选择 "**取消**" 按钮来取消操作，则可以在用户启动另一个操作之前禁用该按钮。 下面的示例演示如何使用[concurrency：： cancellation_token：： register_callback](reference/cancellation-token-class.md#register_callback)方法来注册取消标记被取消时运行的回调函数。

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

文档[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)性介绍了基于值和基于任务的延续之间的差异。 如果未向延续任务提供 `cancellation_token` 对象，则延续通过以下方式从前面的任务继承取消标记：

- 基于值的延续始终继承前面的任务的取消标记。

- 基于任务的延续从不继承前面的任务的取消标记。 使基于任务的延续可取消的唯一方法是显式传递一个取消标记。

这些行为不会受出错任务（即引发异常的任务）影响。 在这种情况下，将取消基于值的延续;基于任务的延续不会被取消。

> [!CAUTION]
> 在另一个任务中创建的任务（即嵌套任务）不会继承父任务的取消标记。 只有基于值的继承延续前面的任务的取消标记。

> [!TIP]
> 当你调用采用 `cancellation_token` 对象的构造函数或函数，并且你不希望可取消该操作时，请使用[concurrency：： cancellation_token：： none](reference/cancellation-token-class.md#none)方法。

还可以向 `task_group` 或 `structured_task_group` 对象的构造函数提供取消标记。 一个重要方面是子任务组继承此取消标记。 有关使用[concurrency：： run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token)函数运行以调用 `parallel_for`来演示此概念的示例，请参阅本文档后面的[取消并行算法](#algorithms)。

[[返回页首](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>取消标记和任务复合

[Concurrency：： when_all](reference/concurrency-namespace-functions.md#when_all)和[concurrency：： when_any](reference/concurrency-namespace-functions.md#when_all)函数可帮助你组合多个任务以实现常见模式。 本节描述这些函数如何与取消标记配合使用。

向 `when_all` 和 `when_any` 函数提供取消标记时，该函数仅当取消标记被取消时，或者当某个参与者任务以 "已取消" 状态结束或引发异常时，才会取消该函数。

不向 `when_all` 函数提供取消标记时，该函数从组合成整体操作的每个任务继承取消标记。 当取消其中的任何标记并且至少有一个参与者任务尚未启动或正在运行时，从 `when_all` 返回的任务将被取消。 当某个任务引发异常时，将会出现类似的行为-从 `when_all` 返回的任务会立即取消并出现该异常。

任务完成时，运行时会选择从 `when_any` 函数返回的任务的取消标记。 如果没有参与任务以已完成状态结束，并且一个或多个任务引发异常，则选择引发的一个任务来完成 `when_any`，并且其标记被选为结束任务的标记。 如果有多个任务以已完成状态结束，则从 `when_any` 任务返回的任务以已完成状态结束。 运行时尝试在完成时选取其标记未被取消的已完成任务，以便 `when_any` 不会被立即取消，则即使其他正在执行的任务可能在以后完成也是如此。

[[返回页首](#top)]

### <a name="cancel"></a>使用 cancel 方法取消并行工作

[Concurrency：： task_group：： cancel](reference/task-group-class.md#cancel)和[concurrency：： structured_task_group：： cancel](reference/structured-task-group-class.md#cancel)方法将任务组设置为已取消状态。 在你调用 `cancel` 之后，任务组不会启动将来的任务。 `cancel` 方法可以由多个子任务调用。 取消的任务会导致[concurrency：： task_group：： wait](reference/task-group-class.md#wait)和[concurrency：： structured_task_group：： wait](reference/structured-task-group-class.md#wait)方法返回[concurrency：：已取消](reference/concurrency-namespace-enums.md#task_group_status)。

如果任务组已取消，则从每个子任务到运行时的调用会触发一个*中断点*，这会导致运行时引发和捕获内部异常类型来取消活动任务。 并发运行时不定义具体的中断点；它们可以在对运行时的任何调用中出现。 运行时必须处理它引发的异常才能执行取消。 因此，不要处理任务正文中的未知异常。

如果子任务执行耗时的操作，并且不会调入运行时，它必须定期检查取消并及时退出。 下面的示例演示一种确定取消工作的时间的方法。 任务 `t4` 在遇到错误时取消父任务组。 任务 `t5` 偶尔调用 `structured_task_group::is_canceling` 方法来检查取消。 如果父任务组已取消，则任务 `t5` 打印一条消息并退出。

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

此示例在任务循环的每个<sup>第</sup>100 次迭代时检查取消。 检查取消的频率取决于任务执行的工作量和你需要任务响应取消的速度。

如果无权访问父任务组对象，请调用[concurrency：： is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling)函数以确定父任务组是否已取消。

`cancel` 方法只影响子任务。 例如，如果取消并行工作树插图中的任务组 `tg1`，则该树中的所有任务（`t1`、`t2`、`t3`、`t4` 和 `t5`）都将受到影响。 如果取消嵌套的任务组 `tg2`，则只有任务 `t4` 和 `t5` 会受到影响。

当你调用 `cancel` 方法时，将同时取消所有子任务组。 但是，取消操作并不影响并行工作树中任务组的任何父级。 下面的示例通过在并行工作树插图中进行生成来演示这一点。

这些示例中的第一个示例为任务 `t4`（该任务是任务组 `tg2` 的子级）创建一个工作函数。 该工作函数在循环中调用函数 `work`。 如果对 `work` 的任何调用失败，则该任务取消其父任务组。 这将导致任务组 `tg2` 进入已取消状态，但不会取消任务组 `tg1`。

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

此第二个示例与第一个示例类似，只不过该任务将取消任务组 `tg1`。 这会影响树中的所有任务（`t1`、`t2`、`t3`、`t4` 和 `t5`）。

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

`structured_task_group` 类不是线程安全的。 因此，调用其父 `structured_task_group` 对象方法的子任务会产生未指定的行为。 此规则的例外情况是 `structured_task_group::cancel` 和[concurrency：： structured_task_group：： is_canceling](reference/structured-task-group-class.md#is_canceling)方法。 子任务可以调用这些方法来取消父任务组和检查取消。

> [!CAUTION]
> 尽管可以使用取消标记来取消由作为 `task` 对象的子级运行的任务组执行的工作，但不能使用 `task_group::cancel` 或 `structured_task_group::cancel` 方法来取消任务组中运行的 `task` 对象。

[[返回页首](#top)]

### <a name="exceptions"></a>使用异常来取消并行工作

要取消并行工作树，使用取消标记和 `cancel` 方法比使用异常处理更有效。 取消标记和 `cancel` 方法由上向下取消任务和所有子任务。 相反，异常处理以自下而上的方式工作，并且必须在异常向上传播时单独取消每个子任务组。 主题[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)说明了并发运行时如何使用异常来传达错误。 但是，并非所有异常都表示错误。 例如，搜索算法可能在找到结果时取消其关联的任务。 但是，如上所述，在取消并行工作时，异常处理的效率比使用 `cancel` 方法低。

> [!CAUTION]
> 如非必要，建议你不要使用异常来取消并行工作。 取消标记和任务组 `cancel` 方法更高效且更不易出错。

当在传递给任务组的工作函数体中引发异常时，运行时存储该异常，并将该异常封送到等待任务组完成的上下文。 与 `cancel` 方法一样，运行时将放弃任何尚未启动的任务，并且不接受新任务。

第三个示例与第二个示例类似，只不过任务 `t4` 引发异常来取消任务组 `tg2`。 此示例使用 `try`-`catch` 块检查任务组 `tg2` 等待其子任务完成时的取消。 与第一个示例类似，这会导致任务组 `tg2` 进入已取消状态，但不会取消任务组 `tg1`。

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

第四个示例使用异常处理来取消整个工作树。 此示例在任务组 `tg1` 等待其子任务完成时（而不是任务组 `tg2` 等待其子任务完成时）捕获异常。 与第二个示例类似，这会导致树中的两个任务组 `tg1` 和 `tg2` 都进入已取消状态。

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

因为 `task_group::wait` 和 `structured_task_group::wait` 方法在子任务引发异常时引发，所以你没有从它们收到返回值。

[[返回页首](#top)]

## <a name="algorithms"></a>取消并行算法

PPL 中的并行算法（如 `parallel_for`）基于任务组生成。 因此，你可以使用许多相同的技术来取消并行算法。

以下示例说明了几种取消并行算法的方法。

下面的示例使用 `run_with_cancellation_token` 函数调用 `parallel_for` 算法。 `run_with_cancellation_token` 函数采用一个取消标记作为参数并同步调用提供的工作函数。 因为并行算法基于任务生成，它们继承父任务的取消标记。 因此，`parallel_for` 可以响应取消。

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

下面的示例使用[concurrency：： structured_task_group：： run_and_wait](reference/structured-task-group-class.md#run_and_wait)方法来调用 `parallel_for` 算法。 `structured_task_group::run_and_wait` 方法等待提供的任务完成。 `structured_task_group` 对象可让工作函数取消该任务。

[!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]

本示例生成以下输出。

```Output
The task group status is: canceled.
```

下面的示例使用异常处理来取消 `parallel_for` 循环。 运行时将异常封送到调用上下文。

[!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]

本示例生成以下输出。

```Output
Caught 50
```

下面的示例使用一个布尔型标志来协调 `parallel_for` 循环中的取消。 每个任务都运行，因为此示例不使用 `cancel` 方法或异常处理来取消整个任务集。 因此，这种技术的计算开销可能比取消机制大。

[!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]

每个取消方法都有其他方法所没有的优点。 请选择适合你的特定需求的方法。

[[返回页首](#top)]

## <a name="when"></a>何时不使用取消

当一组相关任务中的每个成员可以及时退出时，使用取消是恰当的。 但是，在某些情况下取消可能不适合你的应用程序。 例如，由于任务取消是协作性的，如果任何单个任务被阻止，则无法取消整个任务集。 例如，如果一个任务尚未开始，但它取消阻止另一个活动任务，则在任务组已取消时，它将不能启动。 这会导致应用程序中发生死锁。 可能不适合使用取消的另一个示例是任务被取消，但其子任务会执行重要操作（如释放资源）。 因为在取消父任务时整个任务集也会被取消，所以将无法执行此操作。 有关说明这一点的示例，请参阅并行模式库中的最佳实践主题中的[了解取消和异常处理如何影响对象析构](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction)部分。

[[返回页首](#top)]

## <a name="related-topics"></a>相关主题

|标题|说明|
|-----------|-----------------|
|[如何：使用取消来中断并行循环](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|演示如何使用取消来实现并行搜索算法。|
|[如何：使用异常处理来中断并行循环](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|演示如何使用 `task_group` 类编写基本树结构的搜索算法。|
|[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|描述运行时如何处理任务组、轻量级任务和异步代理引发的异常，以及如何在应用程序中响应异常。|
|[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|描述任务与任务组之间的关系，以及如何在应用程序中使用非结构化和结构化的任务。|
|[并行算法](../../parallel/concrt/parallel-algorithms.md)|描述同时对多个数据集合执行工作的并行算法|
|[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|提供对并行模式库的概述。|

## <a name="reference"></a>参考

[task 类（并发运行时）](../../parallel/concrt/reference/task-class.md)

[cancellation_token_source 类](../../parallel/concrt/reference/cancellation-token-source-class.md)

[cancellation_token 类](../../parallel/concrt/reference/cancellation-token-class.md)

[task_group 类](reference/task-group-class.md)

[structured_task_group 类](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for 函数](reference/concurrency-namespace-functions.md#parallel_for)
