---
title: "销毁对话框 | Microsoft Docs"
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
  - "析构, 对话框"
  - "对话框, 删除"
  - "对话框, 销毁"
  - "对话框, 移除"
  - "MFC 对话框, 销毁"
  - "有模式对话框, 销毁"
  - "无模式对话框, 销毁"
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 销毁对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模式对话框时堆栈上帧通常创建和销毁创建其末尾的函数。  当对象超出范围时，对话框对象的析构函数调用。  
  
 无模式对话框是父视图通常创建并拥有或框架窗口 \(应用程序的主框架窗口或文档框架窗口。  默认程序 [DestroyWindow](../Topic/CWnd::DestroyWindow.md)[OnClose](../Topic/CWnd::OnClose.md) 处理调用，也就销毁对话框窗口。  如果对话框仅突出，没有到对象或其他特殊所有权语义的指针，则应该重写 [PostNcDestroy](../Topic/CWnd::PostNcDestroy.md) 销毁 C\+\+ 对话框对象。  还应重写并调用 `DestroyWindow`。它的内部。[OnCancel](../Topic/CDialog::OnCancel.md) 当不再需要时，否则，对话框的所有者应销毁 C\+\+ 对象。  
  
## 请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)