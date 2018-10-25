---
title: 演练： 创建基于代理的应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41ae491a851d2e9a21a57ce35a54590323060881
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070583"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>演练：创建基于代理的应用程序

本主题介绍如何创建基本的基于代理的应用程序。 在本演练中，可以创建一个以异步方式从文本文件读取数据的代理。 应用程序使用 Adler-32 校验和算法来计算该文件的内容的校验和。

## <a name="prerequisites"></a>系统必备

你必须了解要完成本演练的以下主题：

- [异步代理](../../parallel/concrt/asynchronous-agents.md)

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [消息传递函数](../../parallel/concrt/message-passing-functions.md)

- [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a> 部分

本演练演示如何执行以下任务：

- [创建控制台应用](#createapplication)

- [创建 file_reader 类](#createagentclass)

- [在应用程序中使用 file_reader 类](#useagentclass)

##  <a name="createapplication"></a> 创建控制台应用程序

本部分演示如何创建引用该程序将使用的标头文件的 Visual c + + 控制台应用程序。

#### <a name="to-create-a-visual-c-application-by-using-the-win32-console-application-wizard"></a>若要使用 Win32 控制台应用程序向导创建的 Visual c + + 应用程序

1. 上**文件**菜单上，单击**新建**，然后单击**项目**以显示**新项目**对话框。

1. 在中**新的项目**对话框中，选择**Visual c + +** 中的节点**项目类型**窗格，然后选择**Win32 控制台应用程序**在中**模板**窗格。 例如，键入项目的名称`BasicAgent`，然后单击**确定**以显示**Win32 控制台应用程序向导**。

1. 在中**Win32 控制台应用程序向导**对话框中，单击**完成**。

1. 在 stdafx.h 中，添加以下代码。

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   标头文件 agents.h 包含的功能[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)类。

1. 验证应用程序已成功创建，可以通过生成并运行它。 若要在生成应用程序，**构建**菜单上，单击**生成解决方案**。 如果成功生成了应用程序，通过单击运行该应用程序**开始调试**上**调试**菜单。

[[返回页首](#top)]

##  <a name="createagentclass"></a> 创建 file_reader 类

本部分演示如何创建`file_reader`类。 运行时计划每个代理以在其自己的上下文中执行工作。 因此，您可以创建代理以同步方式，执行工作，但以异步方式与其他组件进行交互。 `file_reader`类从给定的输入文件读取数据并将数据从该文件发送到给定的目标组件。

#### <a name="to-create-the-filereader-class"></a>若要创建 file_reader 类

1. 将新的 c + + 头文件添加到你的项目。 为此，请右键单击**标头文件**中的节点**解决方案资源管理器**，单击**添加**，然后单击**新项**。 在中**模板**窗格中，选择**标头文件 (.h)**。 在中**添加新项**对话框中，键入`file_reader.h`中**名称**框，然后单击**添加**。

1. 在 file_reader.h，添加以下代码。

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. 在 file_reader.h，创建一个名为的类`file_reader`派生`agent`。

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. 添加到以下数据成员`private`类的部分。

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   `_file_name`成员是代理从中进行读取的文件名称。 `_target`成员是[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)对象，代理会将写入到文件的内容。 `_error`成员保留代理的生命周期过程中发生任何错误。

1. 添加以下代码`file_reader`构造函数来`public`一部分`file_reader`类。

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   每个构造函数重载设置`file_reader`数据成员。 第二个和第三个构造函数重载使应用程序以对您的代理使用特定计划程序。 第一个重载使用默认计划程序对您的代理。

1. 添加`get_error`方法的公共部分`file_reader`类。

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   `get_error`方法检索代理的生命周期过程中发生任何错误。

1. 实现[2&gt;concurrency::agent::run&lt;2}](reference/agent-class.md#run)中的方法`protected`类的部分。

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

`run`方法打开文件并从中读取数据。 `run`方法使用异常处理来捕获文件处理过程中出现任何错误。

   它将调用此方法将数据从文件中，每次[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函数将该数据发送到目标缓冲区。 它将空字符串发送到其目标缓冲区，以指示处理结束。

下面的示例演示 file_reader.h 的完整内容。

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[返回页首](#top)]

##  <a name="useagentclass"></a> 在应用程序中使用 file_reader 类

本部分演示如何使用`file_reader`类来读取文本文件的内容。 它还演示如何创建[concurrency:: call](../../parallel/concrt/reference/call-class.md)对象，它接收此文件数据并计算其 Adler-32 校验和。

#### <a name="to-use-the-filereader-class-in-your-application"></a>若要在你的应用程序中使用 file_reader 类

1. 在 BasicAgent.cpp，添加以下`#include`语句。

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. 在 BasicAgent.cpp，添加以下`using`指令。

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. 在中`_tmain`函数中，创建[concurrency:: event](../../parallel/concrt/reference/event-class.md)表示处理结束的对象。

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. 创建`call`时更新校验和接收数据时的对象。

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   这`call`还将对象设置`event`对象收到空的字符串，表示处理结束时。

1. 创建`file_reader`test.txt 文件中读取和写入到该文件的内容对象`call`对象。

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. 启动代理，并等待它完成。

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. 等待`call`对象来接收所有数据，并完成。

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. 检查错误的文件读取器。 如果不出现任何错误，计算最终 Adler-32 总和并打印到控制台之和。

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

下面的示例显示了完整的 BasicAgent.cpp 文件。

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[返回页首](#top)]

## <a name="sample-input"></a>示例输入

这是输入的文件 text.txt 示例内容：

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>示例输出

如果使用示例输入，此程序将生成以下输出：

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>可靠编程

若要阻止数据成员的并发访问，我们建议添加执行工作的方法`protected`或`private`类的部分。 仅添加的方法发送或接收消息到或从代理到`public`类的部分。

始终调用[concurrency:: agent:: 完成](reference/agent-class.md#done)方法以将代理移到已完成状态。 通常调用此方法，再从返回`run`方法。

## <a name="next-steps"></a>后续步骤

基于代理的应用程序的另一个示例，请参阅[演练： 使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。

## <a name="see-also"></a>请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)<br/>
[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)<br/>
[演练：使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)

