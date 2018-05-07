---
title: 消息发送和接收 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b7ded8dd0c818b95d6f45a722bd7b8516d48ff1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="message-sending-and-receiving"></a>消息发送和接收
考虑进程的发送部分以及框架响应的方式。  
  
 大多数消息来源于用户与程序的交互。 命令通过以下方式生成：用鼠标单击菜单项或工具栏按钮或按快捷键。 用户还通过一些操作来生成 Windows 消息，例如，通过移动窗口或调整窗口大小。 当发生程序启动或终止、窗口获取或丢失焦点等情况时，会发送其他 Windows 消息。 通过鼠标单击或与用户与控件（如对话框中的按钮或列表框控件）的其他交互来生成控件通知消息。  
  
 **运行**类的成员函数`CWinApp`检索消息并将它们分派到适当的窗口。 大多数命令消息将发送到应用程序的主框架窗口。 由类库预定义的 `WindowProc` 将获取消息并以不同方式传送这些消息，具体取决于所接收消息的类别。  
  
 现在考虑过程的接收部分。  
  
 消息的初始接收器必须为窗口对象。 窗口消息通常由该窗口对象直接处理。 通常源于应用程序的主框架窗口的命令消息将传送到中所述的命令目标链[命令路由](../mfc/command-routing.md)。  
  
 能够接收消息或命令的每个对象都有其自己的消息映射，此映射会将消息或命令与其处理程序的名称配对。  
  
 当命令目标对象接收消息或命令时，它会在其消息映射中搜索匹配项。 如果它找到此消息的处理程序，则会调用该处理程序。 有关如何搜索消息映射的详细信息，请参阅[如何 Framework 搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)。 再次参考图[框架中的命令](../mfc/user-interface-objects-and-command-ids.md)。  
  
## <a name="see-also"></a>请参阅  
 [框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)

