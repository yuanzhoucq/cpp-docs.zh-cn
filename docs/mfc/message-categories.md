---
title: "消息类别 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令消息 [C++]"
  - "控件通知消息"
  - "控件 [MFC], 通知"
  - "消息处理 [C++], 消息类型"
  - "消息 [C++], 类别"
  - "消息 [C++], Windows"
  - "Windows 消息 [C++], 类别"
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 消息类别
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

哪种消息的是您编写处理程序？  有三种主要类别：  
  
1.  Windows 消息  
  
     这包括以 **WM\_** 前缀开头的这些主消息，除了 **WM\_COMMAND**。  窗口消息由窗口和视图的各个处理。  这些消息通常具有用于确定如何处理消息的参数。  
  
2.  控件通知  
  
     这包括来自控件和其他子窗口的 **WM\_COMMAND** 通知消息到其父窗口。  例如，编辑控件发送其父控件通知包含 **EN\_CHANGE** 代码的 **WM\_COMMAND** 消息，当用户执行了可能修改了编辑控件的文本操作。  消息的窗口处理程序响应通知消息用某个适当方式，如检索控件中的文本。  
  
     框架发送与其他 **WM\_** 消息相似的的控件通知消息。  但是，在用户单击它们时，引发异常，该按钮发送的 **BN\_CLICKED** 控件通知信息。  此消息为专门将命令发送消息并与任何其他命令。  
  
3.  命令消息  
  
     这包括从用户界面对象的 **WM\_COMMAND** 通知消息：菜单、工具栏按钮和快捷键。  框架处理命令与其他消息不同，并且，它们可以通过更多对象处理，如 [命令目标](../mfc/command-targets.md)说明。  
  
##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> 窗口消息和控件通知消息  
 在类别 1 和 2 的消息 \- Windows 消息和通知控件 \- 由窗口操作：从类派生类的对象 `CWnd`。  这包括 `CFrameWnd`，`CMDIFrameWnd`，`CMDIChildWnd`，`CView`，`CDialog`，并拥有这些基类派生的类。  这样的对象封装 `HWND`，一个窗口的句柄。  
  
##  <a name="_core_command_messages"></a> 命令消息  
 在类别 3 的消息 \- 命令 \- 可由对象的处理：文档、文档模板和应用程序对象以及窗口和视图之外。  当命令直接影响一些特定对象时，对象处理命令很有意义。  例如，在"文件"菜单中打开命令与应用程序相结合：应用程序打开指定文档时将收到命令。  由于打开命令的处理程序为应用程序类的成员函数。  有关更多有关命令和它们路由到对象的信息，请参见 [Framework 如何通知处理程序](../mfc/how-the-framework-calls-a-handler.md)。  
  
## 请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)