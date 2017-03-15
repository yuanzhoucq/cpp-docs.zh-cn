---
title: "命令和控件通知的处理程序 | Microsoft Docs"
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
  - "命令, 处理程序"
  - "控件 [MFC], 通知"
  - "函数 [C++], 处理程序"
  - "处理程序"
  - "处理程序, 命令"
  - "处理程序, 控件通知"
  - "通知, 用于控件的处理程序"
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 命令和控件通知的处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命令或控件通知消息没有默认的处理程序。  因此，仅由约定命名这些类别的消息处理程序约束。  当映射命令或控件通知给处理程序时，属性窗口建议基于命令 ID 或控件通知代码命名。  可以接受建议的名称，更改或替换它。  
  
 约定建议您在为它们所表示的用户界面对象用全部类别来命名处理程序。  从而可能命名在"编辑"菜单上剪切命令的处理程序  
  
 [!CODE [NVC_MFCMessageHandling#4](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCMessageHandling#4)]  
  
 因为在应用上通常实现了剪切命令，框架为为剪切命令预定义剪切命令 ID为 **ID\_EDIT\_CUT** 。  有关所有预定义命令 ID 的列表，请参阅 AFXRES.H 文件。  有关详细信息，请参阅 [Standard Commands](../mfc/standard-commands.md)。  
  
 此外，约定建议 **BN\_CLICKED** 通知消息的处理程序可能命名来自标记“我的按钮”按钮  
  
 [!CODE [NVC_MFCMessageHandling#5](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCMessageHandling#5)]  
  
 因为它等效于特定的用户界面对象，可能将分配 `IDC_MY_BUTTON` 的命令 ID。  
  
 所有消息类别不采用参数也不返回值。  
  
## 请参阅  
 [声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)