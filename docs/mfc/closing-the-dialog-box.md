---
title: "关闭对话框 | Microsoft Docs"
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
  - "对话框, 关闭"
  - "MFC 对话框, 关闭"
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 关闭对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当用户选择该按钮，通常是"确定"按钮还是"取消按钮之一，所以模式对话框关闭。  选择或取消"按钮时导致窗口发送对话框对象中带有按钮的 ID 的 **BN\_CLICKED** 控件通知消息，**IDOK** 或 **IDCANCEL**。  `CDialog` 为这些消息提供默认处理程序函数：`OnOK` 和 `OnCancel`。  默认处理程序调用 `EndDialog` 成员函数关闭对话框窗口。  还可以从您的代码中调用 `EndDialog`。  有关更多信息，请参见 `CDialog` 类的成员函数[SubclassDlgItem](../Topic/CDialog::EndDialog.md) *MFC 参考*。  
  
 排列关闭和删除非模式对话框，重写 `PostNcDestroy` 并调用 **this** 的指针 **删除** 运算符。  [销毁对话框](../mfc/destroying-the-dialog-box.md) 解释了接下来发生的情况。  
  
## 请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)