---
title: "动画控件发送的通知 | Microsoft Docs"
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
  - "动画控件 [C++], 通知"
  - "CAnimateCtrl 类, 通知"
  - "控件 [MFC], 动画"
  - "通知, 动画控件"
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 动画控件发送的通知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

动画控件 \([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)\) 发送两种不同类型的通知消息。  通知以 [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) 消息的形式发送。  
  
 当动画空间开始播放片段时，发送 [ACN\_START](http://msdn.microsoft.com/library/windows/desktop/bb761891) 消息。  当动画控件完成或停止播放播放片段时，发送 [ACN\_STOP](http://msdn.microsoft.com/library/windows/desktop/bb761893) 消息。  
  
## 请参阅  
 [使用 CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [控件](../mfc/controls-mfc.md)