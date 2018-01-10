---
title: "消息类别 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: be3bc617c0f3a9915c7ae0314b0e3889ecc561f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="message-categories"></a>消息类别
哪种消息编写处理为有三个主要类别：  
  
1.  Windows 消息  
  
     这包括主要开头这些消息**WM_**前缀，除**WM_COMMAND**。 Windows 消息由窗口和视图处理。 这些消息通常具有用于确定如何处理消息的参数。  
  
2.  控件通知  
  
     这包括**WM_COMMAND**从控件和其他子窗口到其父窗口的通知消息。 例如，编辑控件会向其父级发送**WM_COMMAND**消息包含**EN_CHANGE**控件通知代码时用户已执行操作，可能更改编辑控件中的文本。 窗口的消息处理程序将以某种合适的方式响应通知消息，如检索控件中的文本。  
  
     框架将传送控件通知消息，如其他**WM_**消息。 但是，是一个例外， **BN_CLICKED**时在用户单击它们由按钮发送的控件通知消息。 此消息将专门作为命令消息处理，并像传送其他命令一样传送。  
  
3.  命令消息  
  
     这包括**WM_COMMAND**从用户界面对象的通知消息： 菜单、 工具栏按钮和快捷键。 框架处理命令不同于其他消息，并且它们可以处理由多个类型的对象，如中所述[命令目标](../mfc/command-targets.md)。  
  
##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a>Windows 消息和控件通知消息  
 类别 1 和 2 的消息（Windows 消息和控件通知）由窗口处理：派生自 `CWnd` 对象。 这包括 `CFrameWnd`、`CMDIFrameWnd`、`CMDIChildWnd`、`CView`、`CDialog`，并且您拥有派生自这些基类的类。 此类对象将封装 `HWND`（Windows 窗口的句柄）。  
  
##  <a name="_core_command_messages"></a>命令消息  
 类别 3 的消息（命令）可由更多类型的对象处理：文档、文档模板和应用程序对象本身以及窗口和视图。 当命令直接影响了某个特定对象时，让该对象处理命令很有意义。 例如，“文件”菜单上的“打开”命令与应用程序逻辑关联：应用程序在收到命令时打开指定的文档。 因此，“打开”命令的处理程序是应用程序类的成员函数。 命令和如何传送到对象的详细信息，请参阅[框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)。  
  
## <a name="see-also"></a>请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)

