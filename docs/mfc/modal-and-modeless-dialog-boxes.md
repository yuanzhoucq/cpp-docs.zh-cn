---
title: "模式和无模式对话框 | Microsoft Docs"
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
  - "MFC 对话框, 有模式"
  - "MFC 对话框, 无模式"
  - "有模式对话框"
  - "无模式对话框"
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 模式和无模式对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用 [CDialog](../mfc/reference/cdialog-class.md) 类管理两个对话框：  
  
-   *模式对话框*，要求用户在继续之前响应程序  
  
-   *无模式对话框*，在屏幕上并保持随时可供使用，但允许其他用户活动  
  
 创建的对话框模板资源编辑和方法相同模式和无模式对话框中。  
  
 创建程序的对话框需要以下步骤：  
  
1.  使用 [对话框编辑器](../mfc/dialog-editor.md) 设计对话框和创建自己的对话框模板资源。  
  
2.  创建对话框类。  
  
3.  连接对话框类中的 [对话框的消息处理程序的资源管理](../mfc/adding-event-handlers-for-dialog-box-controls.md)。  
  
4.  将数据成员与对话框的控件和控件指定和 [对话框数据交换](../mfc/dialog-data-exchange.md)[对话框数据验证](../mfc/dialog-data-validation.md)。  
  
## 请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)