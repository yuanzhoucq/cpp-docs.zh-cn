---
title: 如何：创建使用特定计划程序策略的代理
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: ece6b113e3fe10c2c3179517f73137df281acf87
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141739"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>如何：创建使用特定计划程序策略的代理

代理是一种应用程序组件，它与其他组件异步工作以解决更多计算任务。 代理通常具有设定的生命周期并维护状态。

每个代理都有唯一的应用程序要求。 例如，启用用户交互（检索输入或显示输出）的代理可能需要更高优先级的计算资源访问权限。 计划程序策略使你能够控制计划程序在管理任务时使用的策略。 本主题演示如何创建使用特定计划程序策略的代理。

有关将自定义计划程序策略与异步消息块结合使用的基本示例，请参阅[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。

本主题使用异步代理库中的功能，例如代理、消息块和消息传递函数来执行工作。 有关异步代理库的详细信息，请参阅[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。

## <a name="example"></a>示例

下面的示例定义了从[concurrency：： agent](../../parallel/concrt/reference/agent-class.md)： `permutor` 和 `printer`派生的两个类。 `permutor` 类计算给定输入字符串的所有排列。 `printer` 类将进度消息输出到控制台。 `permutor` 类执行计算密集型操作，此操作可能会使用所有可用的计算资源。 若要有用，`printer` 类必须及时打印每个进度消息。

为了使 `printer` 类公平访问计算资源，此示例使用[如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)中描述的步骤来创建具有自定义策略的计划程序实例。 自定义策略将线程优先级指定为最高优先级的类。

为了说明使用具有自定义策略的计划程序的优点，此示例执行了两次总体任务。 该示例首先使用默认计划程序来计划这两个任务。 然后，该示例使用默认计划程序来计划 `permutor` 对象，并使用一个计划程序，该计划程序具有用于计划 `printer` 对象的自定义策略。

[!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]

本示例生成以下输出。

```Output
With default scheduler:
Computing all permutations of 'Grapefruit'...
100% complete...

With higher context priority:
Computing all permutations of 'Grapefruit'...
100% complete...
```

尽管这两组任务都生成相同的结果，但使用自定义策略的版本允许 `printer` 对象以提升的优先级运行，使其行为更对象。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `permute-strings.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc permute-strings**

## <a name="see-also"></a>另请参阅

[计划程序策略](../../parallel/concrt/scheduler-policies.md)<br/>
[异步代理](../../parallel/concrt/asynchronous-agents.md)
