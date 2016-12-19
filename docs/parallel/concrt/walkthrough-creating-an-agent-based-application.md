---
title: "演练：创建基于代理的应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "异步代理, 正在创建"
  - "agent 类，示例"
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
caps.latest.revision: 24
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：创建基于代理的应用程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题描述如何创建基于代理的基本应用程序。  在本演练中，您可以创建以异步方式从文本文件读取数据的代理。  应用程序使用 Adler\-32 校验和算法计算该文件的内容校验和。  
  
## 系统必备  
 若要完成本演练，必须了解以下主题：  
  
-   [异步代理](../../parallel/concrt/asynchronous-agents.md)  
  
-   [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [消息传递函数](../../parallel/concrt/message-passing-functions.md)  
  
-   [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a> 各节内容  
 本演练演示如何执行以下任务：  
  
-   [创建控制台应用程序](#createApplication)  
  
-   [创建 file\_reader 类](#createAgentClass)  
  
-   [在应用程序中使用 file\_reader 类](#useAgentClass)  
  
##  <a name="createApplication"></a> 创建控制台应用程序  
 本节演示如何创建一个引用该程序将使用的头文件的 Visual C\+\+ 控制台应用程序。  
  
#### 通过使用 Win32 控制台应用程序向导创建 Visual C\+\+ 应用程序  
  
1.  在**“文件”**菜单上，单击**“新建”**，再单击**“项目”**以显示**“新建项目”**对话框。  
  
2.  在**“新建项目”**对话框中，选择**“项目类型”**窗格中的**“Visual C\+\+”**节点，然后选择**“模板”**窗格中的**“Win32 控制台应用程序”**。  键入项目名称，例如 `BasicAgent`，然后单击**“确定”**以显示**“Win32 控制台应用程序向导”**。  
  
3.  在**“Win32 控制台应用程序向导”**中，单击**“完成”**。  
  
4.  在 stdafx.h 中，添加下列代码。  
  
     [!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_1.h)]  
  
     头文件 agents.h 包含 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 类的功能。  
  
5.  通过生成并运行应用程序来验证该应用程序已成功创建。  若要生成应用程序，请在**“生成”**菜单上单击**“生成解决方案”**。  如果成功生成了该应用程序，请单击**“调试”**菜单上的**“开始调试”**来运行该应用程序。  
  
 \[[Top](#top)\]  
  
##  <a name="createAgentClass"></a> 创建 file\_reader 类  
 本节演示如何创建 `file_reader` 类。  运行时安排每个代理在其自己的上下文中执行工作。  因此，您可以创建以同步方式执行工作但以异步方式与其他组件进行交互的代理。  `file_reader` 类读取给定输入文件中的数据，并将该文件中的数据发送到给定的目标组件。  
  
#### 创建 file\_reader 类  
  
1.  将新的 C\+\+ 头文件添加到您的项目中。  若要执行此操作，请在**“解决方案资源管理器”**中右击**“头文件”**节点，单击**“添加”**，再单击**“新建项”**。  在**“模板”**窗格中选择**“头文件\(.h\)”**。  在**“添加新项”**对话框内的**“名称”**框中键入 `file_reader.h`，然后单击**“添加”**。  
  
2.  在 file\_reader.h 中添加以下代码。  
  
     [!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_2.h)]  
  
3.  在 file\_reader.h 中，创建名为 `file_reader` 的类，该类是从 `agent` 中派生的。  
  
     [!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_3.h)]  
  
4.  将以下数据成员添加到您的类的 `private` 节中。  
  
     [!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_4.h)]  
  
     `_file_name` 成员是代理从中进行读取的文件名。  `_target` 成员是代理向其写入文件内容的 [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) 对象。  `_error` 成员将保存在代理生命期内发生的任何错误。  
  
5.  将 `file_reader` 构造函数的以下代码添加到 `file_reader` 类的 `public` 节中。  
  
     [!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_5.h)]  
  
     每个构造函数重载都将设置 `file_reader` 数据成员。  第二个和第三个构造函数重载使您的应用程序能够对您的代理使用特定的计划程序。  第一个重载对您的代理使用默认计划程序。  
  
6.  将 `get_error` 方法添加到 `file_reader` 类的 public 节中。  
  
     [!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_6.h)]  
  
     `get_error` 方法将检索在代理生命期内发生的任何错误。  
  
7.  在您类的 `protected` 部分实现 [concurrency::agent::run](../Topic/agent::run%20Method.md) 方法。  
  
     [!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_7.h)]  
  
     `run` 方法将打开该文件，并读取其中的数据。  `run` 方法使用异常处理功能捕获文件处理过程中发生的任何错误。  
  
     每次该方法从文件读取数据时，它都会调用 [concurrency::asend](../Topic/asend%20Function.md) 函数以将该数据发送至目标缓冲区。  它会将空字符串发送到其目标缓冲区以指示处理结束。  
  
 下面的示例演示了 file\_reader.h 的完整内容。  
  
 [!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_8.h)]  
  
 \[[Top](#top)\]  
  
##  <a name="useAgentClass"></a> 在应用程序中使用 file\_reader 类  
 本节演示如何使用 `file_reader` 类读取文本文件的内容。  它还演示如何创建接收该文件数据并计算其 Adler\-32 校验和的 [concurrency::call](../../parallel/concrt/reference/call-class.md) 对象。  
  
#### 在应用程序中使用 file\_reader 类  
  
1.  在 BasicAgent.cpp 中，添加下面的 `#include` 语句。  
  
     [!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_9.cpp)]  
  
2.  在 BasicAgent.cpp 中，添加下面的 `using` 指令。  
  
     [!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_10.cpp)]  
  
3.  在 `_tmain` 函数中，创建发送处理结束信号的 [concurrency::event](../../parallel/concrt/reference/event-class.md) 对象。  
  
     [!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_11.cpp)]  
  
4.  创建一个在接收数据时更新校验和的 `call` 对象。  
  
     [!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_12.cpp)]  
  
     此 `call` 对象在收到空字符串时还将设置 `event` 对象，以通知处理结束。  
  
5.  创建 `file_reader` 对象，该对象从文件 test.txt 中进行读取并将该文件的内容写入到 `call` 对象。  
  
     [!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_13.cpp)]  
  
6.  启动代理并等待其完成。  
  
     [!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_14.cpp)]  
  
7.  等待 `call` 对象接收所有数据并完成。  
  
     [!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_15.cpp)]  
  
8.  检查文件读取器是否有错误。  如果没有发生错误，则计算最终的 Adler\-32 总和并将该总和打印到控制台。  
  
     [!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_16.cpp)]  
  
 下面的示例演示了完整的 BasicAgent.cpp 文件。  
  
 [!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_17.cpp)]  
  
 \[[Top](#top)\]  
  
## 示例输入  
 以下是输入文件 text.txt 的示例内容：  
  
  **The quick brown fox**  
**jumps**  
**over the lazy dog**   
## 示例输出  
 与示例输入结合使用时，此程序将生成以下输出：  
  
  **Adler\-32 总和为 fefb0d75**   
## 可靠编程  
 为了防止同时访问数据成员，我们建议您将执行工作的方法添加到类的 `protected` 或 `private` 节中。  仅将向代理发送消息或从代理接收消息的方法添加到类的 `public` 节中。  
  
 始终调用 [concurrency::agent::done](../Topic/agent::done%20Method.md) 方法以将代理移至已完成状态。  通常在从 `run` 方法返回之前调用此方法。  
  
## 后续步骤  
 有关基于代理的应用程序的另一个示例，请参见[演练：使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。  
  
## 请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)   
 [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)   
 [演练：使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)