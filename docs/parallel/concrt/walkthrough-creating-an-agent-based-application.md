---
title: 演练：创建基于代理的应用程序
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 20197786e3d3c2d34d29af748c1cc073902cf70d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377448"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>演练：创建基于代理的应用程序

本主题介绍如何创建基于代理的基本应用程序。 在本演练中，您可以创建一个代理，该代理以异步方式从文本文件读取数据。 应用程序使用 Adler-32 校验和算法计算该文件内容的校验和。

## <a name="prerequisites"></a>先决条件

您必须了解以下主题才能完成本演练：

- [异步代理](../../parallel/concrt/asynchronous-agents.md)

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [消息传递函数](../../parallel/concrt/message-passing-functions.md)

- [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>部分

本演练演示如何执行以下任务：

- [创建控制台应用](#createapplication)

- [创建file_reader类](#createagentclass)

- [在应用程序中使用file_reader类](#useagentclass)

## <a name="creating-the-console-application"></a><a name="createapplication"></a>创建控制台应用程序

本节演示如何创建C++控制台应用程序，该应用程序引用程序将使用的标头文件。 初始步骤因您使用的 Visual Studio 版本而异。 要查看您首选版本的 Visual Studio 的文档，请使用**版本**选择器控件。 它位于此页面的目录顶部。

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>在 Visual Studio 2019 中创建C++控制台应用程序

1. 在主菜单中，选择“文件”“新建”“项目”，打开“创建新项目”对话框**** > **** > ********。

1. 在对话框顶部，将“语言”**** 设置为“C++”****，将“平台”**** 设置为“Windows”****，并将“项目类型”**** 设置为“控制台”****。

1. 从筛选的项目类型列表中，选择“控制台应用”，然后选择“下一步”********。 在下一页中，输入`BasicAgent`为项目的名称，并根据需要指定项目位置。

1. 选择“创建”**** 按钮创建项目。

1. 右键单击**解决方案资源管理器**中的项目节点，然后选择**属性**。 在**配置属性** > **C/C++** > **预编译标头** > **下，预编译标头**选择 **"创建**"。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>在 Visual Studio 2017 和更早版本中创建C++控制台应用程序

1. 在"**文件**"菜单上，单击 **"新建**"，然后单击 **"项目**"以显示 **"新项目**"对话框。

1. 在"**新项目**"对话框中，在 **"项目类型**"窗格中选择 **"可视C++"** 节点，然后在 **"模板"** 窗格中选择**Win32 控制台应用程序**。 键入项目的名称，例如 ，`BasicAgent`然后单击 **"确定"** 以显示**Win32 控制台应用程序向导**。

1. 在**Win32 控制台应用程序向导**对话框中，单击"**完成**"。

::: moniker-end

1. 在*pch.h（Visual* Studio 2017 和更早版本中的*stdafx.h）* 中，添加以下代码：

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   标头文件代理.h 包含[并发：：代理](../../parallel/concrt/reference/agent-class.md)类的功能。

1. 通过生成并运行应用程序，验证应用程序是否成功创建。 要生成应用程序，请在 **"生成"** 菜单上单击 **"生成解决方案**"。 如果应用程序生成成功，则通过单击 **"调试"** 菜单上的 **"开始调试**"来运行应用程序。

[[顶部](#top)]

## <a name="creating-the-file_reader-class"></a><a name="createagentclass"></a>创建file_reader类

本节演示如何创建类`file_reader`。 运行时计划每个代理在其自己的上下文中执行工作。 因此，您可以创建同步执行工作的代理，但与其他组件异步交互。 类`file_reader`从给定的输入文件读取数据，并将数据从该文件发送到给定的目标组件。

#### <a name="to-create-the-file_reader-class"></a>创建file_reader类

1. 向项目添加新C++头文件。 为此，请右键单击**解决方案资源管理器**中的 **"标题文件**"节点，单击"**添加**"，然后单击 **"新项目**"。 在 **"模板"** 窗格中，选择 **"标题文件 "（.h）**。 在"**添加新项目"** 对话框中，在`file_reader.h`**"名称"** 框中键入，然后单击"**添加**"。

1. 在 file_reader.h 中，添加以下代码。

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. 在 file_reader.h 中，创建派生自`file_reader``agent`的命名类。

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. 将以下数据成员添加到类的`private`部分。

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   成员`_file_name`是代理从中读取的文件名。 成员`_target`是一个[并发：：ITarget](../../parallel/concrt/reference/itarget-class.md)对象，代理将文件的内容写入。 成员`_error`保留在代理生命周期内发生的任何错误。

1. 将构造函数的`file_reader`以下代码添加到`public``file_reader`类的节。

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   每个构造函数重载设置`file_reader`数据成员。 第二个和第三个构造函数重载使应用程序能够将特定的计划程序与代理一起使用。 第一个重载使用默认计划程序与代理。

1. 将`get_error`方法添加到`file_reader`类的公共部分。

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   该方法`get_error`检索代理生命周期期间发生的任何错误。

1. 在类`protected`的节中实现[并发：：代理：：运行](reference/agent-class.md#run)方法。

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

该方法`run`打开文件并从中读取数据。 该方法`run`使用异常处理来捕获文件处理期间发生的任何错误。

   每次此方法从文件中读取数据时，它调用[并发：：asend](reference/concurrency-namespace-functions.md#asend)函数以将数据发送到目标缓冲区。 它将空字符串发送到其目标缓冲区，以指示处理的结束。

下面的示例显示了 file_reader.h 的完整内容。

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[顶部](#top)]

## <a name="using-the-file_reader-class-in-the-application"></a><a name="useagentclass"></a>在应用程序中使用file_reader类

本节演示如何使用 类`file_reader`读取文本文件的内容。 它还演示如何创建[并发：：调用](../../parallel/concrt/reference/call-class.md)对象，该对象接收此文件数据并计算其 Adler-32 校验和。

#### <a name="to-use-the-file_reader-class-in-your-application"></a>在应用程序中使用file_reader类

1. 在 BasicAgent.cpp 中，`#include`添加以下语句。

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. 在 BasicAgent.cpp 中，`using`添加以下指令。

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. 在`_tmain`函数中，创建一个[并发：：事件](../../parallel/concrt/reference/event-class.md)对象，该对象表示处理结束的信号。

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. 创建在`call`接收数据时更新校验和的对象。

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   此`call`对象在接收空`event`字符串时还会设置对象以发出处理结束的信号。

1. 创建从`file_reader`文件 test.txt 读取的对象，并将该文件的内容写入`call`对象。

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. 启动代理并等待它完成。

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. 等待`call`对象接收所有数据并完成。

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. 检查文件读取器是否存在错误。 如果未发生错误，请计算最终的 Adler-32 总和，并将总和打印到控制台。

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

下面的示例显示了完整的 BasicAgent.cpp 文件。

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[顶部](#top)]

## <a name="sample-input"></a>示例输入

这是输入文件文本.txt 的示例内容：

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>示例输出

当与示例输入一起使用时，此程序会产生以下输出：

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>可靠编程

为了防止对数据成员的并发访问，我们建议您向类 的`protected`或`private`部分添加执行工作的方法。 仅将发送或接收消息的方法发送到类的`public`子部分或从代理发送到类的分区。

始终调用[并发：：代理：:d一](reference/agent-class.md#done)种将代理移动到已完成状态的方法。 通常，在从 方法返回之前调用`run`此方法。

## <a name="next-steps"></a>后续步骤

有关基于代理的应用程序的另一个示例，请参阅[演练：使用联接来防止死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。

## <a name="see-also"></a>另请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)<br/>
[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)<br/>
[演练：使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
