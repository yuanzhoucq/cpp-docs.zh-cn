---
title: "框架中的命令和消息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- events [MFC], command routing in MFC
- event-driven programming [MFC]
- events [MFC], event-driven programming
- message-driven programming [MFC]
ms.assetid: d799ed8c-6a9f-4f05-be5d-29cb5bc6d185
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 390f094b05994dcf2b3b2351a24f163b06554f84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="messages-and-commands-in-the-framework"></a>框架中的消息和命令
为 Microsoft Windows 编写的应用程序是"驱动的消息。" 在响应鼠标单击、 击键、 窗口动作数等的事件，Windows 将消息发送到适当的窗口。 Framework 应用程序处理 Windows 消息与适用于 Windows 的任何其他应用程序一样。 但该框架还提供一些增强功能使处理消息更轻松、 更易于维护，并更好地封装。  
  
 下面的主题介绍使用文章系列的其余部分中讨论的消息和命令的主要术语：  
  
-   [消息](../mfc/messages.md)  
  
-   [消息处理程序](../mfc/message-handlers.md)  
  
-   [消息类别](../mfc/message-categories.md)  
  
-   [Windows 消息和控件通知消息](../mfc/message-categories.md)  
  
-   [命令消息](../mfc/message-categories.md)  
  
-   [消息映射](../mfc/mapping-messages.md)  
  
-   [用户界面对象和命令 Id](../mfc/user-interface-objects-and-command-ids.md)  
  
-   [命令目标](../mfc/command-targets.md)  
  
## <a name="see-also"></a>请参阅  
 [消息处理和映射](../mfc/message-handling-and-mapping.md)

