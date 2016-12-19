---
title: "Using Task Manager | Microsoft Docs"
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
  - "断点, Task Manager"
  - "调试 [ATL], using Task Manager"
  - "Task Manager"
ms.assetid: 773fccd5-308d-42c2-a17f-60ae94989062
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using Task Manager
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

其中一种简单的方法调试服务是使用Windows NT 4.0或Windows 2000的任务管理器。  在服务运行时，启动任务管理器并单击 **Processes** 选项。  右击EXE的名称然后单击 **Debug**。  这将启动Visual C\+\+附加到该进程中运行。  现在，在允许您的 **Debug** 菜单中单击 **Break** 在代码中设置断点。  单击 **Run** 运行到已选定断点。  
  
## 请参阅  
 [Debugging Tips](../atl/debugging-tips.md)