---
title: "Displaying Assertions | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "断言, 调试"
  - "断言, 显示"
  - "调试 [ATL], displaying assertions"
  - "调试断言"
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Displaying Assertions
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果客户端连接到的服务看似停止响应，服务可以断言和显示的消息框不能发现。  若要确认此使用Visual C\+\+的调试器调试代码\(请参见 [使用任务管理器](../atl/using-task-manager.md) 本节前面）。  
  
 如果您确定您的服务公开看不到消息框，您可能希望在再次使用服务之前设置 **Allow Service to Interact with Desktop** 选项。  此选项是允许服务公开的任何消息框在桌面上的一个启动参数。  若要设置此选项，请打开服务控制面板应用程序，选择服务，单击 **Startup**，然后选择 **Allow Service to Interact with Desktop** 选项。  
  
## 请参阅  
 [Debugging Tips](../atl/debugging-tips.md)