---
title: "如何：在状态栏中显示命令信息 | Microsoft Docs"
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
  - "显示命令状态"
  - "提示 [C++]"
  - "状态栏, 显示命令信息"
  - "状态栏, 消息区域"
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 如何：在状态栏中显示命令信息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在运行应用程序向导创建应用程序的主干时，您可以支持在工具栏和状态栏。  在应用程序向导的可支持两个。  将状态栏存在，则应用程序自动提供有用反馈，当用户将指针移动到项上在菜单上。  当选中菜单项，显示突出时，在应用程序状态栏将自动显示一个提示字符串。  例如，在中，当用户将指针移到 **剪切** 命令的指针在 **编辑** 菜单时，状态栏在剪贴板可能显示“选择剪切并将其放入”在状态栏的消息大小。  提示来帮助用户了解菜单项的目的。  当用户单击工具栏按钮，这也有效。  
  
 可以添加到该状态栏帮助您通过定义添加到程序的菜单项的提示字符串。  在编辑菜单项的属性。菜单编辑器时，若要执行此操作，请提供的提示字符串。  您定义的字符串在应用程序资源文件存储；它们具有与命令它们解释的 ID。  
  
 默认情况下，应用程序向导将 `AFX_IDS_IDLEMESSAGE`标准的，ID“准备”消息，显示，当程序等待新消息时。  如果在应用程序向导指定上下文相关帮助选项，消息为“更改对于帮助，按 F1”。  
  
## 请参阅  
 [消息处理和映射](../mfc/message-handling-and-mapping.md)