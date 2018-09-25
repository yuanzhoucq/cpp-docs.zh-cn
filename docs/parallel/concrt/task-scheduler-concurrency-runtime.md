---
title: 任务计划程序 （并发运行时） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- oversubscription [Concurrency Runtime]
- task scheduler [Concurrency Runtime], oversubscription
- schedule groups [Concurrency Runtime]
- task scheduler [Concurrency Runtime], lightweight tasks
- task scheduler [Concurrency Runtime]
- lightweight tasks [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler policies
- task scheduler [Concurrency Runtime], schedule groups
- wait function [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler instances
- scheduler instances [Concurrency Runtime]
- scheduler policies [Concurrency Runtime]
- task scheduler [Concurrency Runtime], wait function
ms.assetid: 9aba278c-e0c9-4ede-b7c6-fedf7a365d90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56f7f35169b349abb5f7db14b3f3a749ab7dd673
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419732"
---
# <a name="task-scheduler-concurrency-runtime"></a>任务计划程序（并发运行时）

文档这一部分的主题介绍并发运行时任务计划程序的重要功能。 如果希望细微调整并发运行时的现有代码的性能，则任务计划程序会很有用。

> [!IMPORTANT]
>  任务计划程序不可以从通用 Windows 平台 (UWP) 应用。 有关详细信息，请参阅[创建异步操作在 c + + UWP 应用的](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。
>
>  在 Visual Studio 2015 及更高版本， [concurrency:: task](../../parallel/concrt/reference/task-class.md)类和 ppltasks.h 中的相关的类型使用 Windows 线程池作为其计划程序。 本主题不再适用于在 ppltasks.h 中定义的类型。 并行算法（例如 parallel_for）继续使用并发运行时作为默认计划程序。

> [!TIP]
>  并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 因为任务计划程序可帮助您优化您的应用程序的性能，我们建议您开始[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)你是否新并发运行时。

任务计划程序在运行时计划和协调任务。 一个*任务*是执行特定作业的工作单元。 任务通常可以与其他任务并行运行。 任务组项、并行算法和异步代理所执行的工作都属于任务示例。

任务计划程序可以管理关于在具有多个计算资源的计算机上高效执行计划任务的详细信息。 任务计划程序还使用基础操作系统的最新功能。 因此，使用并发运行时的应用程序会自动缩放，并提高具有扩展功能的硬件性能。

[将与其他并发模型进行比较](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)介绍抢先式和协作式计划机制之间的差异。 任务计划程序将操作系统的抢先式计划程序与协作式计划和工作窃取算法配合使用，以达到处理资源的最大使用率。

并发运行时提供了默认计划程序，因此你无需管理基础结构详细信息。 因此，通常不会直接使用任务计划程序。 但是，为了满足应用程序的质量要求，你可以使用任务计划程序提供自己的计划策略或将计划程序与特定任务相关联。 例如，假设你有一个作用范围不超过四个处理器的并行排序例程。 可以使用*计划程序策略*若要创建的计划程序生成不超过四个并发任务。 通过在此计划程序上运行排序例程，可使其他活动计划程序使用剩余的任何处理资源。

## <a name="related-topics"></a>相关主题

|标题|描述|
|-----------|-----------------|
|[计划程序实例](../../parallel/concrt/scheduler-instances.md)|介绍计划程序实例以及如何使用 `concurrency::Scheduler` 和 `concurrency::CurrentScheduler` 类来管理它们。 当希望将显式计划策略与特定类型的工作负荷相关联时，可使用计划程序实例。|
|[计划程序策略](../../parallel/concrt/scheduler-policies.md)|介绍计划程序策略的角色。 当希望控制计划程序在管理任务时使用的策略时，可使用计划程序策略。|
|[计划组](../../parallel/concrt/schedule-groups.md)|介绍计划组的角色。 当你需要在任务之间处于较高位置时（例如，当一组相关的任务受益于在相同的处理器节点上执行操作时），可使用计划组。|
|[轻量级任务](../../parallel/concrt/lightweight-tasks.md)|介绍轻量级任务的角色。 当改编现有代码以使用并发运行时的计划功能时，轻量级任务非常有用。|
|[上下文](../../parallel/concrt/contexts.md)|介绍上下文的角色、`concurrency::wait` 函数和 `concurrency::Context` 类。 如果你需要对上下文何时阻止、取消阻止和生成进行控制，或者你希望何时在应用程序中启用超额订阅进行控制，请使用此功能。|
|[内存管理函数](../../parallel/concrt/memory-management-functions.md)|介绍 `concurrency::Alloc` 和 `concurrency::Free` 函数。 通过以并发方式分配和释放内存，这些函数可以提高内存性能。|
|[将与其他并发模型进行比较](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|介绍抢先式和协作式计划机制之间的差异。|
|[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|介绍如何在应用程序中使用各种并行模式（例如并行算法）。|
|[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)|介绍如何在应用程序中使用异步代理。|
|[并发运行时](../../parallel/concrt/concurrency-runtime.md)|描述可以简化并发编程并包含相关主题链接的并发运行时。|

