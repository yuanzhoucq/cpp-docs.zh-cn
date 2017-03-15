---
title: "将 Windows 消息映射到您的类 | Microsoft Docs"
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
  - "映射, 消息到对话框类"
  - "消息映射 [C++], 在对话框类中"
  - "消息映射 [C++], 将 Windows 消息映射到类"
  - "消息到对话框类"
  - "消息到对话框类, 映射"
  - "MFC 对话框, Windows 消息"
  - "Windows 消息 [C++], 在对话框类中映射"
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 将 Windows 消息映射到您的类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果需要处理对话框窗口消息，请重写适当处理程序函数。  为此，请使用"属性"窗口设置为 [消息映射](../mfc/reference/mapping-messages-to-functions.md) 到对话框类。  这编写每个消息的消息映射项并将消息处理程序添加成员函数添加到该类。  使用 Visual C\+\+ 源代码编辑器编写在消息处理程序的代码。  
  
 还可以重写，特别是为 [CWnd](../mfc/reference/cwnd-class.md)[CDialog](../mfc/reference/cdialog-class.md) 及其基类的成员函数。  
  
## 您想进一步了解什么？  
  
-   [消息处理和映射](../mfc/message-handling-and-mapping.md)  
  
-   [经常重写的成员函数](../mfc/commonly-overridden-member-functions.md)  
  
-   [经常添加的成员函数](../mfc/commonly-added-member-functions.md)  
  
## 请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)