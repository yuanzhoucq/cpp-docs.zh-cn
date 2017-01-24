---
title: "创建模式对话框 | Microsoft Docs"
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
  - "MFC 对话框, 创建"
  - "MFC 对话框, 有模式"
  - "有模式对话框, 创建"
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建模式对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建模式对话框，调用在 [CDialog](../mfc/reference/cdialog-class.md)中声明的两个公共构造函数之一。  接下来，调用对话框对象的 [DoModal](../Topic/CDialog::DoModal.md) 成员函数显示对话框和管理与其的交互，直至用户选择OK或取消。  由 `DoModal` 管理是使对话框模式化。  对于模式对话框， `DoModal` 加载对话框资源。  
  
## 请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)