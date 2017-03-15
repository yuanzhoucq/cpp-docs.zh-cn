---
title: "处理标题控件通知 | Microsoft Docs"
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
  - "CHeaderCtrl 类, 处理通知"
  - "控件 [MFC], 标题"
  - "标题控件通知"
  - "标题控件, 处理通知"
  - "通知, 针对 CHeaderCtrl 的处理"
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 处理标题控件通知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Views 或对话框类，请使用属性窗口创建与 switch 语句中 [OnChildNotify](../Topic/CWnd::OnChildNotify.md) 处理程序函数要处理的所有的标题控件 \([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\) 通知消息 \(参见 [指向函数的信息映射](../mfc/reference/mapping-messages-to-functions.md)\)。  通知发送到父窗口，该窗口在用户单击或双击项标头时，各个项之间的一条分隔线，等等。  
  
 通知消息与标题控件不包括在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [标题控件引用](http://msdn.microsoft.com/library/windows/desktop/bb775239) 列出。  
  
## 请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控件](../mfc/controls-mfc.md)