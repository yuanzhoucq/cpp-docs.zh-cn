---
title: "无界限 Rich Edit 控件 | Microsoft Docs"
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
  - "无界限 Rich Edit 控件"
  - "CRichEditCtrl 类, 无界限"
  - "Rich Edit 控件, 无界限"
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 无界限 Rich Edit 控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

应用程序可以调整丰富的编辑控件 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\)，由于需要，以便始终相同大小与其内容。  丰富的编辑控件将通过向其父窗口支持此所谓的“无底”功能 [EN\_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787983) 通知消息，只要其内容的大小更改。  
  
 当处理 **EN\_REQUESTRESIZE** 通知消息时，应用程序应将控件的大小调整到指定的 [REQRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787950) 结构的大小。  应用程序在高度可能在控件周围移动任何信息也将更改。  若要调整控件，可以使用 `CWnd` 函数[SetWindowPos](../Topic/CWnd::SetWindowPos.md)。  
  
 使用 [RequestResize](../Topic/CRichEditCtrl::RequestResize.md) 成员函数，可以强制进行无底的 Rich Edit 控件发送 **EN\_REQUESTRESIZE** 通知消息。  此消息会很有用在[OnSize](../Topic/CWnd::OnSize.md) 处理程序中。  
  
 使用 `SetEventMask` 成员函数中，接收 **EN\_REQUESTRESIZE** 通知消息，则必须启用通知。  
  
## 请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)