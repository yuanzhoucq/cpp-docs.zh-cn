---
title: 消息处理和映射
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
ms.openlocfilehash: a27f8220055630873b02dd7ff975c04744ad9e8e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622409"
---
# <a name="message-handling-and-mapping"></a>消息处理和映射

本文章系列介绍 MFC 框架如何处理消息和命令以及您如何将这些消息和命令与其处理程序函数相关联。

在传统的 Windows 程序中，Windows 消息在窗口过程中的大型 switch 语句中处理。 MFC 改为使用[消息映射](message-categories.md)将直接消息映射到不同的类成员函数。 从这方面来看，消息映射比虚函数效率更高，并且前者可让消息由最合适的 C++ 对象（应用程序、文档、视图等）处理。 您可以映射单个消息，或者映射一系列消息、命令 ID 或控件 ID。

WM_COMMAND 消息（通常会由菜单、工具栏按钮或快捷键生成）也使用消息映射机制。 MFC 定义程序中应用程序、框架窗口、视图和活动文档之间的命令消息的标准[路由](command-routing.md)。 如果需要，您可以重写此路由。

消息映射还提供了一种更新用户界面对象（如菜单和工具栏按钮）的方法，即启用或禁用这些对象以适应当前上下文。

有关 Windows 中的消息和消息队列的常规信息，请参阅 Windows SDK 中的[消息和消息队列](/windows/win32/winmsg/messages-and-message-queues)。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [框架中的消息和命令](messages-and-commands-in-the-framework.md)

- [框架如何调用消息处理程序](how-the-framework-calls-a-handler.md)

- [框架如何搜索消息映射](how-the-framework-searches-message-maps.md)

- [声明消息处理程序函数](declaring-message-handler-functions.md)

- [将消息映射到函数](reference/mapping-messages-to-functions.md)

- [如何在状态栏中显示命令信息](how-to-display-command-information-in-the-status-bar.md)

- [用户界面对象的动态更新](how-to-update-user-interface-objects.md)

- [如何：为模板类创建消息映射](how-to-create-a-message-map-for-a-template-class.md)

## <a name="see-also"></a>另请参阅

[概念](mfc-concepts.md)<br/>
[常规 MFC 主题](general-mfc-topics.md)<br/>
[CWnd 类](reference/cwnd-class.md)<br/>
[CCmdTarget 类](reference/ccmdtarget-class.md)
