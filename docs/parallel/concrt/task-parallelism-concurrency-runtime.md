---
title: 任务并行度（并发运行时）
ms.date: 11/04/2016
helpviewer_keywords:
- structured task groups [Concurrency Runtime]
- structured tasks [Concurrency Runtime]
- task groups [Concurrency Runtime]
- task parallelism
- tasks [Concurrency Runtime]
ms.assetid: 42f05ac3-2098-494a-ba84-737fcdcad077
ms.openlocfilehash: 634b4b584e997007a7de72e23c9b16e937a694ae
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143322"
---
# <a name="task-parallelism-concurrency-runtime"></a>任务并行度（并发运行时）

在并发运行时中，*任务*是执行特定作业并通常与其他任务并行运行的工作单元。 任务可分解为多个更细化的任务，这些任务组织成*任务组*。

编写异步代码，并希望在异步操作完成之后进行某种操作时，可使用任务。 例如，可以使用任务以异步方式读取文件，然后使用另一个任务（在本文档后面*将对此*进行说明），以便在数据可用后处理数据。 相反，可以使用任务组将并行工作分解成较小的各部分。 例如，假设你有一个将剩余工作划分为两个分区的递归算法。 可以使用任务组并发运行这两个分区，然后等待划分的工作完成。

> [!TIP]
> 如果要以并行方式将同一例程应用于集合的每个元素，请使用并行算法，如[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)，而不是任务或任务组。 有关并行算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="key-points"></a>关键点

- 通过引用将变量传递到 Lambda 表达式时，必须保证该变量的生存期在任务完成之前一直保持。

- 编写异步代码时，请使用任务（ [concurrency：： task](../../parallel/concrt/reference/task-class.md)类）。 任务类使用 Windows 线程池作为其计划程序中，而不是并发运行时。

- 如果要将并行工作分解成较小的部分，然后等待这些较小的部分完成，请使用任务组（ [concurrency：： task_group](reference/task-group-class.md)类或[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法）。

- 使用[concurrency：： task：： then](reference/task-class.md#then)方法可创建延续。 *延续*是在另一个任务完成后以异步方式运行的任务。 可以连接任意数量的延续以形成异步工作链。

- 基于任务的延续始终计划为在先行任务完成时执行，甚至是在先行任务取消或引发异常时执行。

- 使用[concurrency：： when_all](reference/concurrency-namespace-functions.md#when_all)创建一个任务，该任务在一组任务的每个成员完成后完成。 使用[concurrency：： when_any](reference/concurrency-namespace-functions.md#when_any)创建一个任务，该任务在一组任务的一个成员完成后完成。

- 任务和任务组可以参与并行模式库 (PPL) 取消机制。 有关详细信息，请参阅[PPL 中的取消](cancellation-in-the-ppl.md)操作。

- 若要了解运行时如何处理任务和任务组引发的异常，请参阅[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

## <a name="in-this-document"></a>文档内容

- [使用 Lambda 表达式](#lambdas)

- [Task 类](#task-class)

- [延续任务](#continuations)

- [基于值与基于任务的继续](#value-versus-task)

- [撰写任务](#composing-tasks)

    - [When_all 函数](#when-all)

    - [When_any 函数](#when-any)

- [延迟的任务执行](#delayed-tasks)

- [任务组](#task-groups)

- [比较 task_group 与 structured_task_group](#comparing-groups)

- [示例](#example)

- [可靠的编程](#robust)

## <a name="lambdas"></a>使用 Lambda 表达式

由于其语法简洁，因此 lambda 表达式是定义由任务和任务组执行的工作的常用方法。 下面是一些使用提示：

- 因为任务通常在后台线程上运行，所以在 Lambda 表达式中捕获变量时请注意对象生存期。 如果通过值捕获变量，则会在 lambda 体中创建该变量的副本。 通过引用捕获时，不创建副本。 因此，请确保通过引用捕获的任何变量的生存期长于使用它的任务。

- 将 lambda 表达式传递给任务时，不捕获通过引用在堆栈上分配的变量。

- 应明确在 lambda 表达式中捕获的变量，以便可以确定通过值与通过引用捕获的内容。 因此我们建议不要将 `[=]` 或 `[&]` 选项用于 lambda 表达式。

一种常用模式是将延续链中的一个任务分配给变量，而另一个任务读取该变量。 无法通过值捕获，因为每个延续任务会保存变量的不同副本。 对于堆栈分配的变量，也无法通过引用捕获，因为变量可能不再有效。

若要解决此问题，请使用智能指针（如[std：： shared_ptr](../../standard-library/shared-ptr-class.md)）包装变量并按值传递智能指针。 这样，基础对象便可以进行分配和读取，并且生存期会长于使用它的任务。 即使在变量是 Windows 运行时对象的指针或引用计数的句柄 (`^`) 时，也可使用此技术。 下面是一个基本示例：

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)。

## <a name="task-class"></a>Task 类

您可以使用[concurrency：： task](../../parallel/concrt/reference/task-class.md)类将任务组合到一组从属操作中。 *延续*的概念支持此组合模型。 使用延续可以在上一个任务或*前面*的任务完成时执行代码。 先行任务的结果会作为输入传递给一个或多个延续任务。 先行任务完成时，在等待它的所有延续任务都计划进行执行。 每个延续任务都会收到先行任务结果的副本。 这些延续任务进而也可能是其他延续的先行任务，从而形成任务链。 延续可帮助创建任务间具有特定依赖关系的任意长度的任务链。 此外，任务还可以在其他任务开始之前或是在其他任务运行期间以协作方式参与取消。 有关此取消模型的详细信息，请参阅[PPL 中的取消](cancellation-in-the-ppl.md)操作。

`task` 是模板类。 类型参数 `T` 是由任务生成的结果的类型。 如果任务不返回值，则此类型可以是 `void`。 `T` 不能使用 `const` 修饰符。

当你创建任务时，你将提供执行任务正文的*工作函数*。 此工作函数采用 lambda 函数、函数指针或函数对象的形式。 若要等待任务完成而不获取结果，请调用[concurrency：： task：： wait](reference/task-class.md#wait)方法。 `task::wait` 方法返回一个[concurrency：： task_status](reference/concurrency-namespace-enums.md#task_group_status)值，该值描述任务是否已完成或已取消。 若要获取任务的结果，请调用[concurrency：： task：： get](reference/task-class.md#get)方法。 此方法调用 `task::wait` 以等待任务完成，因此会在结果可用之前阻止当前线程的执行。

下面的示例演示如何创建任务、等待其结果并显示其值。 本文档中的示例使用 lambda 函数，因为它们提供更简洁的语法。 不过你也可以在使用任务时使用函数指针和函数对象。

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

使用[concurrency：： create_task](reference/concurrency-namespace-functions.md#create_task)函数时，可以使用 `auto` 关键字，而不是声明类型。 例如，请考虑创建和打印单位矩阵的以下代码：

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

可以使用 `create_task` 函数创建等效操作。

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

如果在任务执行期间引发异常，则运行时会在对 `task::get` 或 `task::wait` 或是基于任务的延续的后续调用中封送该异常。 有关任务异常处理机制的详细信息，请参阅[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

有关使用 `task`、 [concurrency：： task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)、取消的示例，请参阅[演练：使用任务和 XML HTTP 请求进行连接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)。 （本文档稍后会介绍 `task_completion_event` 类。）

> [!TIP]
> 若要了解特定于 uwp 应用中的任务的详细信息，请参阅[ C++中的异步编程](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)和在[中C++为 UWP 应用创建异步操作](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。

## <a name="continuations"></a>延续任务

在异步编程中，一个异步操作在完成时调用另一个操作并将数据传递到其中的情况非常常见。 传统上，这使用回调方法来完成。 在并发运行时中，*延续任务*提供了相同的功能。 延续任务（也简称为 "延续"）是一个异步任务，由另一个任务（称为*前面*的任务）在前面的任务完成时调用。 使用延续可以：

- 将数据从前面的任务传递到延续。

- 指定调用或不调用延续所依据的精确条件。

- 在延续启动之前取消延续，或在延续正在运行时以协作方式取消延续。

- 提供有关应如何计划延续的提示。 （这仅适用于通用 Windows 平台（UWP）应用。 有关详细信息，请参阅[ C++为 UWP 应用创建异步操作](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。

- 从同一前面的任务中调用多个延续。

- 在多个先行任务中的全部或任意任务完成时调用一个延续。

- 将延续依次相连，形成任意长度。

- 使用延续来处理先行引发的异常。

这些功能使你可以在第一个任务完成时执行一个或多个任务。 例如，可以创建在第一个任务从磁盘读取文件之后压缩文件的延续。

下面的示例修改了上一个示例，以使用[concurrency：： task：： then](reference/task-class.md#then)方法来计划在任务可用时打印前面的任务的值的延续任务。

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

可以按任意长度链接和嵌套任务。 一个任务还可以具有多个延续。 下面的示例演示将上一个任务的值增加三倍的基本延续链。

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

延续还可以返回另一个任务。 如果没有取消，则此任务会在后续延续之前执行。 此方法称为*异步解包*。 要在后台执行其他工作，但不想当前任务阻止当前线程时，异步解包会很有用。 （这在 UWP 应用中很常见，在这种情况下，延续可以在 UI 线程上运行）。 下面的示例演示三个任务。 第一个任务返回在延续任务之前运行的另一个任务。

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
> 当任务的延续返回 `N` 类型的嵌套任务时，生成的任务具有 `N` 类型（而不是 `task<N>`），会在嵌套任务完成时完成。 换句话说，延续会执行嵌套任务的解包。

## <a name="value-versus-task"></a>基于值与基于任务的继续

对于其返回类型是 `task` 的 `T` 对象，可以向其延续任务提供 `T` 或 `task<T>` 类型的值。 采用类型 `T` 的继续称为*基于值的延续*。 基于值的延续计划在先行任务完成而未出现错误并且未取消时执行。 采用类型 `task<T>` 作为参数的继续称为*基于任务的继续符*。 基于任务的延续始终计划为在先行任务完成时执行，甚至是在先行任务取消或引发异常时执行。 随后然后调用 `task::get` 以获取先行任务的结果。 如果前面的任务已取消，`task::get` 会引发[concurrency：： task_canceled](../../parallel/concrt/reference/task-canceled-class.md)。 如果先行任务引发了异常，则 `task::get` 会再次引发该异常。 基于任务的延续在先行任务取消时不会标记为已取消。

## <a name="composing-tasks"></a>撰写任务

本节介绍[concurrency：： when_all](reference/concurrency-namespace-functions.md#when_all)和[concurrency：： when_any](reference/concurrency-namespace-functions.md#when_all)函数，它们可帮助你组合多个任务以实现常见模式。

### <a name="when-all"></a>When_all 函数

`when_all` 函数生成在任务集完成之后完成的任务。 此函数返回 std：：[vector](../../standard-library/vector-class.md)对象，其中包含集合中每个任务的结果。 下面的基本示例使用 `when_all` 创建一个表示三个其他任务完成的任务。

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
> 传递给 `when_all` 的任务必须统一。 换句话说，它们必须全部返回相同类型。

还可以使用 `&&` 语法生成在任务集完成之后完成的任务，如下面的示例所示。

`auto t = t1 && t2; // same as when_all`

可将延续与 `when_all` 结合使用以在任务集完成之后执行操作，这十分常见。 下面的示例将上面的示例修改为打印各自生成 `int` 结果的三个任务的总和。

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

在此示例中，还可以指定 `task<vector<int>>` 以生成基于任务的延续。

如果任务集中的任何任务取消或引发异常，则 `when_all` 会立即完成，不等待其余任务完成。 如果引发异常，则运行时会在你对 `task::get` 返回的任务对象调用 `task::wait` 或 `when_all` 时再次引发异常。 如果有多个任务引发，则运行时会选择其中之一。 因此，请确保在所有任务完成之后观察到所有异常；未经处理的任务异常会导致应用终止。

下面是可以用于确保程序观察到所有异常的实用工具函数。 对于处于提供的范围内的每个任务，`observe_all_exceptions` 会触发再次引发的任何异常，然后会吞并该异常。

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

考虑使用C++和 XAML 的 UWP 应用，并将一组文件写入磁盘。 下面的示例演示如何使用 `when_all` 和 `observe_all_exceptions` 确保该程序观察到所有异常。

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>运行此示例的步骤

1. 在 MainPage.xaml 中，添加一个 `Button` 控件。

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. 在 MainPage.xaml.h 中，将这些前向声明添加到 `private` 类声明的 `MainPage` 节。

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. 在 MainPage.xaml.cpp 中，实现 `Button_Click` 事件处理程序。

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. 在 MainPage.xaml.cpp 中，实现 `WriteFilesAsync`，如示例所示。

> [!TIP]
> `when_all` 是生成 `task` 作为其结果的的非阻止函数。 与[任务：： wait](reference/task-class.md#wait)不同，在 ASTA （应用程序 STA）线程上的 UWP 应用中调用此函数是安全的。

### <a name="when-any"></a>When_any 函数

`when_any` 函数生成在任务集中的第一个任务完成时完成的任务。 此函数返回[std：:p air](../../standard-library/pair-structure.md)对象，该对象包含已完成任务的结果和该任务在集中的索引。

`when_any` 函数在以下情境中尤其有用：

- 冗余运算。 请考虑可以用多种方式执行的算法或运算。 你可使用 `when_any` 函数来选择先完成的运算，然后取消剩余的运算。

- 交叉运算。 你可启动必须全部完成的多项运算，并使用 `when_any` 函数在每项运算完成时处理结果。 在一项运算完成后，可以启动一个或多个其他任务。

- 受限制的运算。 你可使用 `when_any` 函数通过限制并发运算的数量来扩展前面的情境。

- 过期的运算。 你可使用 `when_any` 函数在一个或多个任务与特定时间后完成的任务间进行选择。

与 `when_all` 一样，可使用具有 `when_any` 的延续以在任务集中的第一个任务完成时执行操作，这十分常见。 下面的基本示例使用 `when_any` 创建一个在三个其他任务中的第一个任务完成时完成的任务。

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

在此示例中，还可以指定 `task<pair<int, size_t>>` 以生成基于任务的延续。

> [!NOTE]
> 与 `when_all` 一样，传递给 `when_any` 的任务必须返回相同类型。

还可以使用 `||` 语法生成在任务集中的第一个任务完成之后完成的任务，如下面的示例所示。

`auto t = t1 || t2; // same as when_any`

> [!TIP]
> 与 `when_all`一样，`when_any` 是非阻塞的，可以安全地在 ASTA 线程上的 UWP 应用中调用。

## <a name="delayed-tasks"></a>延迟的任务执行

有时需要延迟任务的执行，直到满足条件，或开始一项任务来响应外部事件。 例如，在异步编程中，可能必须启动任务以响应 I/O 完成事件。

实现此目的的两种方法是使用延续，或启动任务并在任务的工作函数内等待某个事件。 但是在某些情况下，无法使用以上方法之一。 例如，若要创建延续，必须具有先行任务。 但是，如果你没有前面的任务，则可以创建*任务完成事件*，稍后将完成事件链接到前面的任务（如果任务可用）。 此外，因为正在等待的任务也会阻止线程，所以可以使用任务完成事件在异步操作完成时执行工作，从而释放线程。

[Concurrency：： task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)类有助于简化这类任务。 与 `task` 类一样，类型参数 `T` 是由任务生成的结果的类型。 如果任务不返回值，则此类型可以是 `void`。 `T` 不能使用 `const` 修饰符。 通常会将 `task_completion_event` 对象提供给在它的值可用时向它发信号的线程或任务。 同时，一个或多个任务设置为该事件的侦听器。 设置事件时，侦听器任务完成，其延续会计划运行。

有关使用 `task_completion_event` 实现在延迟后完成的任务的示例，请参阅[如何：创建在延迟后完成的任务](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)。

## <a name="task-groups"></a>任务组

*任务组*组织任务的集合。 任务组会将任务推送到工作窃取队列。 计划程序从此队列中删除任务，然后在可用计算资源上执行它们。 将任务添加到任务组之后，可以等待所有任务完成或取消尚未开始的任务。

PPL 使用[concurrency：： task_group](reference/task-group-class.md)和[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)类来表示任务组，并使用[concurrency：： task_handle](../../parallel/concrt/reference/task-handle-class.md)类来表示在这些组中运行的任务。 `task_handle` 类封装执行工作的代码。 与 `task` 类一样，工作函数采用 lambda 函数、函数指针或函数对象的形式。 通常不需要直接使用 `task_handle` 对象。 而是将工作函数传递给任务组，然后任务组会创建和管理 `task_handle` 对象。

PPL 将任务组分为以下两个类别：*非结构化任务组*和*结构化任务组*。 PPL 使用 `task_group` 类表示非结构化任务组，使用 `structured_task_group` 类表示结构化任务组。

> [!IMPORTANT]
> PPL 还定义[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法，该算法使用 `structured_task_group` 类并行执行一组任务。 因为 `parallel_invoke` 算法具有更简洁的语法，所以我们建议尽可能使用它而不是 `structured_task_group` 类。 主题[并行算法](../../parallel/concrt/parallel-algorithms.md)详细介绍 `parallel_invoke`。

当你具有要同时执行的多个独立任务，并且你必须等待所有任务完成才能继续时，可使用 `parallel_invoke`。 此方法通常称为*分叉和联接*并行度。 当你具有要同时执行的多个独立任务，但是要在以后等待任务完成时，可使用 `task_group`。 例如，可以将任务添加到 `task_group` 对象，并在另一个函数中或从另一个线程等待任务完成。

任务组支持取消概念。 取消使你可以向所有活动任务发出信号，表示你要取消整个操作。 取消还可以阻止尚未开始的任务开始。 有关取消的详细信息，请参阅[PPL 中的取消](cancellation-in-the-ppl.md)操作。

运行时还提供了一个异常处理模型，使你可以从任务引发异常，并在等待关联任务组完成时处理该异常。 有关此异常处理模型的详细信息，请参阅[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

## <a name="comparing-groups"></a>比较 task_group 与 structured_task_group

虽然我们建议你使用 `task_group` 或 `parallel_invoke` 而不是 `structured_task_group` 类，不过有一些你要使用 `structured_task_group` 的情况，例如当你编写执行可变数量的任务或需要取消支持的并行算法时。 此部分介绍 `task_group` 与 `structured_task_group` 类之间的差异。

`task_group` 类是线程安全的。 因此，可以从多个线程将任务添加到 `task_group` 对象，然后从多个线程等待或取消 `task_group` 对象。 `structured_task_group` 对象的构造和析构必须在相同词法范围内进行。 此外，对 `structured_task_group` 对象执行的所有操作必须在相同线程上进行。 此规则的例外情况是[concurrency：： structured_task_group：： cancel](reference/structured-task-group-class.md#cancel)和[concurrency：： structured_task_group：： is_canceling](reference/structured-task-group-class.md#is_canceling)方法。 子任务可以随时调用这些方法以取消父任务组或检查是否存在取消。

调用[concurrency：： task_group：： wait](reference/task-group-class.md#wait)或[concurrency：： task_group：： run_and_wait](reference/task-group-class.md#run_and_wait)方法之后，可以在 `task_group` 对象上运行其他任务。 相反，如果在调用[concurrency：： structured_task_group：： wait](reference/structured-task-group-class.md#wait)或[concurrency：： structured_task_group：： run_and_wait](reference/structured-task-group-class.md#run_and_wait)方法之后在 `structured_task_group` 对象上运行其他任务，则该行为是不确定的。

因为 `structured_task_group` 类不会在线程间同步，所以它的执行开销比 `task_group` 类更少。 因此，如果你的问题不需要从多个线程计划工作并且你无法使用 `parallel_invoke` 算法，则 `structured_task_group` 类可帮助你编写更好的执行代码。

如果在另一个 `structured_task_group` 对象内使用一个 `structured_task_group` 对象，则内部对象必须在外部对象完成之前完成并销毁。 `task_group` 类不要求嵌套任务组在外部组完成之前完成。

非结构化任务组和结构化任务组以不同方式处理任务句柄。 可以将工作函数直接传递给 `task_group` 对象；`task_group` 对象会为你创建并管理任务句柄。 `structured_task_group` 类要求你为每个任务管理 `task_handle` 对象。 每个 `task_handle` 对象必须在其关联 `structured_task_group` 对象的整个生存期内保持有效。 使用[concurrency：： make_task](reference/concurrency-namespace-functions.md#make_task)函数创建 `task_handle` 对象，如下面的基本示例所示：

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

若要在具有可变数量任务的情况下管理任务句柄，请使用堆栈分配例程（如[_malloca](../../c-runtime-library/reference/malloca.md)或容器类，如 std：：[vector](../../standard-library/vector-class.md)）。

`task_group` 和 `structured_task_group` 都支持取消。 有关取消的详细信息，请参阅[PPL 中的取消](cancellation-in-the-ppl.md)操作。

## <a name="example"></a> 示例

下面的基本示例演示如何使用任务组。 此示例使用 `parallel_invoke` 算法并发执行两个任务。 每个任务都将子任务添加到一个 `task_group` 对象。 请注意，`task_group` 类允许多个任务同时向它添加任务。

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

以下是此示例的示例输出：

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

因为 `parallel_invoke` 算法并发运行任务，所以输出消息的顺序可能会有所不同。

有关演示如何使用 `parallel_invoke` 算法的完整示例，请参阅[如何：使用 Parallel_invoke 编写并行排序例程](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)和[如何：使用 Parallel_invoke 执行并行操作](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)。 有关使用 `task_group` 类实现异步先期备货的完整示例，请参阅[演练：实现先期](../../parallel/concrt/walkthrough-implementing-futures.md)情况。

## <a name="robust"></a>可靠的编程

请确保了解取消和异常处理在使用任务、任务组和并行算法时的角色。 例如，在并行工作树中，取消的任务会阻止子任务运行。 如果一个子任务执行的操作对于应用程序很重要（如释放资源），则这可能会导致问题。 此外，如果子任务引发异常，则该异常可以通过对象析构函数进行传播，在应用程序中导致不明确的行为。 有关说明这些要点的示例，请参阅并行模式库文档中的最佳实践中的[了解取消和异常处理如何影响对象析构](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction)部分。 有关 PPL 中的取消和异常处理模型的详细信息，请参阅[取消](../../parallel/concrt/cancellation-in-the-ppl.md)和[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

## <a name="related-topics"></a>相关主题

|职务|说明|
|-----------|-----------------|
|[如何：使用 parallel_invoke 来编写并行排序例程](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|演示如何使用 `parallel_invoke` 算法提高双调排序算法的性能。|
|[如何：使用 parallel_invoke 来执行并行操作](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|演示如何使用 `parallel_invoke` 算法提高对共享数据源执行多项操作的程序的性能。|
|[如何：创建在延迟一段时间后完成的任务](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|演示如何使用 `task`、`cancellation_token_source`、`cancellation_token`和 `task_completion_event` 类来创建在延迟一段时间后完成的任务。|
|[演练：实现 Future](../../parallel/concrt/walkthrough-implementing-futures.md)|演示如何在并发运行时中将现有功能合并为执行更多操作的功能。|
|[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|介绍 PPL，它提供用于开发并发应用程序的命令式编程模型。|

## <a name="reference"></a>参考

[task 类（并发运行时）](../../parallel/concrt/reference/task-class.md)

[task_completion_event 类](../../parallel/concrt/reference/task-completion-event-class.md)

[when_all 函数](reference/concurrency-namespace-functions.md#when_all)

[when_any 函数](reference/concurrency-namespace-functions.md#when_any)

[task_group 类](reference/task-group-class.md)

[parallel_invoke 函数](reference/concurrency-namespace-functions.md#parallel_invoke)

[structured_task_group 类](../../parallel/concrt/reference/structured-task-group-class.md)
