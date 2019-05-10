---
title: 如何：创建使用特定计划程序策略的代理
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: 5aac86801015549b5552b51c06a30f8398346a06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411365"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>如何：创建使用特定计划程序策略的代理

代理是以异步方式与其他组件以解决较大的计算任务的应用程序组件。 代理通常已设置的生命周期和维护状态。

每个代理都可能具有唯一的应用程序要求。 例如，可让用户交互 （检索输入或显示输出） 的代理可能需要更高优先级访问计算资源。 计划程序策略让你控制管理任务时，计划程序使用的策略。 本主题演示如何创建使用特定计划程序策略的代理。

使用异步消息块以及自定义计划程序策略的基本示例，请参阅[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。

本主题使用通过异步代理库，例如代理、 消息块和消息传递函数的功能来执行工作。 有关异步代理库的详细信息，请参阅[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。

## <a name="example"></a>示例

下面的示例定义两个类派生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md):`permutor`和`printer`。 `permutor`类计算给定输入字符串的所有排列。 `printer`类将打印到控制台的进度消息。 `permutor`类执行一个计算密集型操作，这可能会使用所有可用的计算资源。 若要很有用，`printer`类必须及时地打印每个进度消息。

若要提供`printer`类对计算资源的公平访问，此示例使用中所述的步骤[如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)来创建具有自定义策略的计划程序实例。 自定义策略指定的线程优先级别是最高的优先级类。

为了说明使用的计划程序的自定义策略的好处，此示例执行整个任务两次。 该示例首先使用默认计划程序来计划这两项任务。 该示例然后使用默认计划程序计划`permutor`对象，并且具有自定义策略来计划的计划程序`printer`对象。

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

尽管这两组任务生成相同的结果，但使用的自定义策略的版本，`printer`对象，以便它响应能力更强的行为在提升的优先级别运行。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`permute-strings.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc permute strings.cpp**

## <a name="see-also"></a>请参阅

[计划程序策略](../../parallel/concrt/scheduler-policies.md)<br/>
[异步代理](../../parallel/concrt/asynchronous-agents.md)
