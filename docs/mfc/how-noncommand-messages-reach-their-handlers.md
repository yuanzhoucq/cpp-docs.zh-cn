---
title: "非命令消息如何到达其处理程序 | Microsoft Docs"
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
  - "消息处理 [C++], 非命令消息"
  - "消息 [C++], 路由"
  - "非命令消息"
  - "Windows 消息 [C++], 路由"
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 非命令消息如何到达其处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

与命令，标准 Windows 消息没有通过命令系统目标。路由，但是由窗口发送消息的窗口通常处理。  窗口可能是主框架窗口、MDI 子窗口、标准控件、对话框、视图，或者子窗口。  
  
 在运行时，所有 Windows 窗口附加到有自己关联的和消息映射处理程序函数的窗口对象 \(直接或间接从 `CWnd`派生\)。  框架使用消息映射\) \- 关于为命令 \- 映射传入消息给处理程序。  
  
## 请参阅  
 [框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)