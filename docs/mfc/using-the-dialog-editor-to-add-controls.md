---
title: "使用对话框编辑器添加控件 | Microsoft Docs"
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
  - "公共控件 [C++], 添加"
  - "控件 [MFC], 添加到对话框"
  - "对话框控件 [C++], 添加到对话框"
  - "对话框编辑器, 创建控件"
  - "Windows 公共控件 [C++], 添加"
ms.assetid: d3f9f994-7e54-4656-a545-42c204557c36
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用对话框编辑器添加控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当您创建时与 [对话框编辑器](../mfc/dialog-editor.md)的对话框模板资源，则控件将调色板的控件拖放到对话框。  这将该控件类型的规范到对话框模板资源。  当构造对话框对象并调用它的 `DoModal` 或 **创建** 成员函数时，框架创建 Windows 控件并将其放在对话框窗口屏幕的。  
  
 如果需要，可以在 [手动创建控件](../mfc/adding-controls-by-hand.md)。  这更多工作。  
  
## 请参阅  
 [创建和使用控件](../mfc/making-and-using-controls.md)   
 [控件](../mfc/controls-mfc.md)