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
ms.openlocfilehash: 686d5eef4aaa67785aa56133d820b637fbf4bb86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364757"
---
# <a name="message-categories"></a>消息类别

您为其中编写处理程序的种类有三个主要类别：

1. Windows 消息

   这主要包括那些以**WM_** 前缀开头的消息，但WM_COMMAND。 Windows 消息由窗口和视图处理。 这些消息通常具有用于确定如何处理消息的参数。

1. 控制通知

   这包括从控件和其他子窗口到其父窗口的 WM_COMMAND 通知消息。 例如，当用户已执行可能更改编辑控件中的文本的操作时，编辑控件会向其父级发送包含 EN_CHANGE 控件通知代码的 WM_COMMAND 消息。 窗口的消息处理程序将以某种合适的方式响应通知消息，如检索控件中的文本。

   框架像其他**WM_** 消息一样路由控制通知消息。 但有一个例外，即用户单击按钮时由按钮发送的 BN_CLICKED 控件通知信息。 此消息将专门作为命令消息处理，并像传送其他命令一样传送。

1. 命令消息

   这包括来自用户界面对象的 WM_COMMAND 通知消息：菜单、工具栏按钮和快捷键。 框架处理命令与其他消息不同，并且它们可以由更多类型的对象处理，如[命令目标中](../mfc/command-targets.md)所述。

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a>窗口消息和控制通知消息

类别 1 和 2 的消息（Windows 消息和控件通知）由窗口处理：派生自 `CWnd` 对象。 这包括 `CFrameWnd`、`CMDIFrameWnd`、`CMDIChildWnd`、`CView`、`CDialog`，并且您拥有派生自这些基类的类。 此类对象将封装 `HWND`（Windows 窗口的句柄）。

## <a name="command-messages"></a><a name="_core_command_messages"></a>命令消息

类别 3 的消息（命令）可由更多类型的对象处理：文档、文档模板和应用程序对象本身以及窗口和视图。 当命令直接影响了某个特定对象时，让该对象处理命令很有意义。 例如，“文件”菜单上的“打开”命令与应用程序逻辑关联：应用程序在收到命令时打开指定的文档。 因此，“打开”命令的处理程序是应用程序类的成员函数。 有关命令及其路由到对象的方式，请参阅[框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)。

## <a name="see-also"></a>另请参阅

[框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)
