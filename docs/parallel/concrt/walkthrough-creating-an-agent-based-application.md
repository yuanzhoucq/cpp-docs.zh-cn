---
title: "演练： 创建基于代理的应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a49c8deb9185b024dfcca977ab229bf594e05101
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-creating-an-agent-based-application"></a>演练：创建基于代理的应用程序
本主题介绍如何创建基于代理的基本应用程序。 在本演练中，你可以创建以异步方式从文本文件中读取数据的代理。 应用程序使用 adler-32 校验和算法来计算该文件的内容的校验和。  
  
## <a name="prerequisites"></a>系统必备  
 你必须了解以下主题来完成本演练：  
  
- [异步代理](../../parallel/concrt/asynchronous-agents.md)  
  
- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [消息传递函数](../../parallel/concrt/message-passing-functions.md)  
  
- [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a> 部分  
 本演练演示如何执行以下任务：  
  
- [创建控制台应用程序](#createapplication)  
  
- [创建 file_reader 类](#createagentclass)  
  
- [应用程序中使用 file_reader 类](#useagentclass)  
  
##  <a name="createapplication"></a>创建控制台应用程序  
 本部分演示如何创建 Visual c + + 控制台应用程序引用此程序将使用的标头文件。  
  
#### <a name="to-create-a-visual-c-application-by-using-the-win32-console-application-wizard"></a>若要使用 Win32 控制台应用程序向导创建 Visual c + + 应用程序  
  
1.  上**文件**菜单上，单击**新建**，然后单击**项目**以显示**新项目**对话框。  
  
2.  在**新项目**对话框中，选择**Visual c + +**中的节点**项目类型**窗格中，然后选择**Win32 控制台应用程序**在**模板**窗格。 为项目键入名称，例如， `BasicAgent`，然后单击**确定**以显示**Win32 控制台应用程序向导**。  
  
3.  在**Win32 控制台应用程序向导**对话框中，单击**完成**。  
  
4.  在 stdafx.h 文件中，添加以下代码。  
  
 [!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]  
  
     标头文件 agents.h 包含的功能[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)类。  
  
5.  验证应用程序已成功创建，可以通过生成并运行它。 若要生成该应用程序，在**生成**菜单上，单击**生成解决方案**。 如果成功生成了应用程序，通过单击运行该应用程序**启动调试**上**调试**菜单。  
  
 [[返回页首](#top)]  
  
##  <a name="createagentclass"></a>创建 file_reader 类  
 本部分演示如何创建`file_reader`类。 运行时计划每个代理在它自己的上下文中执行工作。 因此，你可以创建代理以同步执行工作，但以异步方式与其他组件进行交互。 `file_reader`类从给定的输入文件中读取数据并将该文件中的数据发送到给定的目标组件。  
  
#### <a name="to-create-the-filereader-class"></a>若要创建 file_reader 类  
  
1.  将新的 c + + 头文件添加到你的项目。 为此，请右键单击**标头文件**中的节点**解决方案资源管理器**，单击**添加**，然后单击**新项**。 在**模板**窗格中，选择**标头文件 (.h)**。 在**添加新项**对话框中，键入`file_reader.h`中**名称**中，然后单击**添加**。  
  
2.  在 file_reader.h，添加以下代码。  
  
 [!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]  
  
3.  在 file_reader.h，创建名为的类`file_reader`派生自`agent`。  
  
 [!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]  
  
4.  添加到以下数据成员`private`类的部分。  
  
 [!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]  
  
     `_file_name`成员是代理从中进行读取的文件名称。 `_target`成员是[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)对象代理写入到文件的内容。 `_error`成员包含在代理生命期期间发生任何错误。  
  
5.  添加以下代码`file_reader`构造函数来`public`部分`file_reader`类。  
  
 [!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]  
  
     每个构造函数重载设置`file_reader`数据成员。 第二个和第三个构造函数重载使你的应用程序对您的代理使用特定计划程序。 第一个重载使用默认计划程序对您的代理。  
  
6.  添加`get_error`方法的公共部分`file_reader`类。  
  
 [!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]  
  
     `get_error`方法检索的代理的生命周期内出现的任何错误。  
  

7.  实现[concurrency::agent::run](reference/agent-class.md#run)中的方法`protected`类的部分。  

  
 [!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]  
  
`run`方法打开该文件并读取其中的数据。 `run`方法使用异常处理来捕获文件处理过程中发生任何错误。  
  
   它会调用此方法将数据从文件中，每次[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函数将该数据发送到的目标缓冲区。 它将空字符串发送到其目标缓冲区以指示处理的末尾。  

  
 下面的示例演示 file_reader.h 的完整内容。  
  
 [!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]  
  
 [[返回页首](#top)]  
  
##  <a name="useagentclass"></a>应用程序中使用 file_reader 类  
 本部分演示如何使用`file_reader`类来读取文本文件的内容。 它还演示如何创建[concurrency:: call](../../parallel/concrt/reference/call-class.md)接收此文件数据并计算其 adler-32 校验和的对象。  
  
#### <a name="to-use-the-filereader-class-in-your-application"></a>若要在你的应用程序中使用 file_reader 类  
  
1.  在 BasicAgent.cpp，添加以下`#include`语句。  
  
 [!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]  
  
2.  在 BasicAgent.cpp，添加以下`using`指令。  
  
 [!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]  
  
3.  在`_tmain`函数中，创建[concurrency:: event](../../parallel/concrt/reference/event-class.md)发出信号处理末尾的对象。  
  
 [!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]  
  
4.  创建`call`时更新校验和，接收数据时的对象。  
  
 [!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]  
  
     这`call`对象还将设置`event`对象在接收空字符串，以指示处理结束时。  
  
5.  创建`file_reader`对象从 test.txt 文件读取和写入到该文件的内容`call`对象。  
  
 [!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]  
  
6.  启动代理并等待其完成。  
  
 [!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]  
  
7.  等待`call`接收所有数据和完成的对象。  
  
 [!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]  
  
8.  检查错误文件读取器。 如果没有发生错误，计算最终的 adler-32 总和和打印到控制台的总和。  
  
 [!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]  
  
 下面的示例演示完整的 BasicAgent.cpp 文件。  
  
 [!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]  
  
 [[返回页首](#top)]  
  
## <a name="sample-input"></a>示例输入  
 这是输入的文件 text.txt 的示例内容：  
  
```Output  
The quick brown fox  
jumps  
over the lazy dog  
```  
  
## <a name="sample-output"></a>示例输出  
 如果用于示例输入，该程序将生成以下输出：  
  
```Output  
Adler-32 sum is fefb0d75  
```  
  
## <a name="robust-programming"></a>可靠编程  
 若要防止对数据成员的并发访问，我们建议将执行到的工作的方法添加`protected`或`private`类的部分。 仅添加发送或接收到或从代理到消息的方法`public`类的部分。  
  

 始终调用[concurrency:: agent:: 完成](reference/agent-class.md#done)方法以将你的代理移至已完成状态。 你通常调用此方法从返回之前`run`方法。  

  
## <a name="next-steps"></a>后续步骤  
 有关基于代理的应用程序的另一个示例，请参阅[演练： 使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。  
  
## <a name="see-also"></a>请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)   
 [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)   
 [演练：使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)

