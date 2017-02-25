---
title: "消息发送和接收 | Microsoft Docs"
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
  - "控件通知消息"
  - "消息 [C++], MFC"
  - "消息 [C++], 接收"
  - "消息 [C++], 发送"
  - "MFC [C++], 消息"
  - "Windows 消息 [C++], 在 MFC 中处理"
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 消息发送和接收
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

考虑进程中发送的部分，而框架如何响应。  
  
 消息由大多数与程序的用户交互。  命令生成的菜单或工具栏按钮按项的鼠标单击或由快捷键击键。  用户还生成窗口消息，例如，移动它们或调整窗口大小。  其他窗口发送，当事件发生，如程序启动或终止，则获取或窗口失去焦点时，依此类推。  控件通知消息用鼠标单击或其他用户交互生成具有控件，如按钮或列表框控件中的  
  
 类 `CWinApp` 的 **运行** 成员函数检索消息并将它们调度到相应的窗口。  大多数命令发送到应用程序的主框架窗口。  类库预定义的消息 `WindowProc` 接收并根据不同方式发送自己，接收的消息类。  
  
 现在请考虑进程的接收一部分。  
  
 消息初始接收器必须为窗口对象。  窗口消息直接按该窗口对象通常处理。  命令消息通常，自在应用程序主框架窗口，则路由到 [命令传送](../mfc/command-routing.md)描述的命令目标链。  
  
 每个对象获得接收消息或命令有匹配一个消息或命令处理程序名称与其自己的消息映射。  
  
 当命令目标对象接收消息或命令时，会搜索其匹配的消息映射。  如果它找到了有效附属消息处理程序，则调用该处理程序。  有关消息映射如何搜索的更多信息，请参见 [Framework 如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)。  将参考 [框架中的命令](../mfc/user-interface-objects-and-command-ids.md)图。  
  
## 请参阅  
 [框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)