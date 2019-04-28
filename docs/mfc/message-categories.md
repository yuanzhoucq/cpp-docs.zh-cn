---
title: 消息类别
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
ms.openlocfilehash: 07d9e706e8ed01a81ee580e7c4e11fa1f1a7a8df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206875"
---
# <a name="message-categories"></a>消息类别

哪些类型的消息编写处理程序的有三个主要类别：

1. Windows 消息

   这包括主要使用开头的消息**WM_** 前缀，但 WM_COMMAND 除外。 Windows 消息由窗口和视图处理。 这些消息通常具有用于确定如何处理消息的参数。

1. 控件通知

   这包括来自控件和其他子窗口到其父窗口的 WM_COMMAND 通知消息。 例如，一个编辑控件向其父级发送 WM_COMMAND 消息来包含 EN_CHANGE 控件通知代码，当用户已经采取可能已更改文本编辑控件中的操作。 窗口的消息处理程序将以某种合适的方式响应通知消息，如检索控件中的文本。

   框架将传送控件通知消息与其他值一样**WM_** 消息。 一个例外，但是，是当用户单击这些按钮发送的 BN_CLICKED 控件通知消息。 此消息将专门作为命令消息处理，并像传送其他命令一样传送。

1. 命令消息

   这包括来自用户界面对象的 WM_COMMAND 通知消息： 菜单、 工具栏按钮和快捷键。 框架处理命令以不同的方式从其他消息，并且它们可以处理更多类型的对象，如中所述[命令目标](../mfc/command-targets.md)。

##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Windows 消息和控件通知消息

类别 1 和 2 的消息（Windows 消息和控件通知）由窗口处理：派生自 `CWnd` 对象。 这包括 `CFrameWnd`、`CMDIFrameWnd`、`CMDIChildWnd`、`CView`、`CDialog`，并且您拥有派生自这些基类的类。 此类对象将封装 `HWND`（Windows 窗口的句柄）。

##  <a name="_core_command_messages"></a> 命令消息

类别 3 的消息（命令）可由更多类型的对象处理：文档、文档模板和应用程序对象本身以及窗口和视图。 当命令直接影响了某个特定对象时，让该对象处理命令很有意义。 例如，“文件”菜单上的“打开”命令与应用程序逻辑关联：应用程序在收到命令时打开指定的文档。 因此，“打开”命令的处理程序是应用程序类的成员函数。 有关命令和如何传送到对象的详细信息，请参阅[框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)。

## <a name="see-also"></a>请参阅

[框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)
