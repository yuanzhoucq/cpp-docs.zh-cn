---
title: 消息处理和映射 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11ac9e794aef374012f2b15faa7e93b907f6a15c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194536"
---
# <a name="message-handling-and-mapping"></a>消息处理和映射
本文章系列介绍 MFC 框架如何处理消息和命令以及您如何将这些消息和命令与其处理程序函数相关联。  
  
 在传统的 Windows 程序中，Windows 消息在窗口过程中的大型 switch 语句中处理。 而是使用 MFC[消息映射](../mfc/message-categories.md)将直接消息映射到不同的类成员函数。 从这方面来看，消息映射比虚函数效率更高，并且前者可让消息由最合适的 C++ 对象（应用程序、文档、视图等）处理。 您可以映射单个消息，或者映射一系列消息、命令 ID 或控件 ID。  
  
 WM_COMMAND 消息 — 通常由菜单、 工具栏按钮或快捷键生成的也使用消息映射机制。 MFC 定义一个标准[路由](../mfc/command-routing.md)命令之间的消息应用程序，框架窗口、 视图和应用程序中的活动文档。 如果需要，您可以重写此路由。  
  
 消息映射还提供了一种更新用户界面对象（如菜单和工具栏按钮）的方法，即启用或禁用这些对象以适应当前上下文。  
  
 有关消息和消息队列在 Windows 中的常规信息，请参阅[消息和消息队列](https://msdn.microsoft.com/library/windows/desktop/ms632590)Windows SDK 中。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息  
  
-   [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)  
  
-   [框架如何调用消息处理程序](../mfc/how-the-framework-calls-a-handler.md)  
  
-   [框架如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)  
  
-   [声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)  
  
-   [将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)  
  
-   [如何在状态栏中显示命令信息](../mfc/how-to-display-command-information-in-the-status-bar.md)  
  
-   [用户界面对象的动态更新](../mfc/how-to-update-user-interface-objects.md)  
  
-   [如何：为模板类创建消息映射](../mfc/how-to-create-a-message-map-for-a-template-class.md)  
  
## <a name="see-also"></a>请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)   
 [CWnd 类](../mfc/reference/cwnd-class.md)   
 [CCmdTarget 类](../mfc/reference/ccmdtarget-class.md)
