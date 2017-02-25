---
title: "对话框的生命周期 | Microsoft Docs"
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
  - "对话框, 生命周期"
  - "对话框的生命周期"
  - "MFC 对话框, 生命周期"
  - "有模式对话框, 生命周期"
  - "无模式对话框, 生命周期"
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 对话框的生命周期
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在对话框的生命周期中，用户，调用对话框通常在创建并初始化对话框对象的命令处理程序中，用户交互的对话框，并且，关闭对话框。  
  
 对于模式对话框，因而，对话框关闭后，处理程序收集任何数据。用户输入。  因为对话框对象存在，在其 Windows 对话框关闭后，可以使用对话框获取数据的类成员变量。  
  
 对于无模式对话框，则在对话框，可见时，您可能常常从该对话框提取对象的数据。  有时，销毁对话框对象；发生这种情况时依赖代码。  
  
## 您想进一步了解什么？  
  
-   [创建并显示对话框](../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [创建模式对话框](../mfc/creating-modal-dialog-boxes.md)  
  
-   [创建无模式对话框。](../mfc/creating-modeless-dialog-boxes.md)  
  
-   [使用内存中的对话框模板](../mfc/using-a-dialog-template-in-memory.md)  
  
-   [将对话框的背景色](../mfc/setting-the-dialog-box’s-background-color.md)  
  
-   [初始化对话框](../mfc/initializing-the-dialog-box.md)  
  
-   [处理该对话框的消息窗口](../mfc/handling-windows-messages-in-your-dialog-box.md)  
  
-   [从对话框对象检索数据](../mfc/retrieving-data-from-the-dialog-object.md)  
  
-   [关闭对话框](../mfc/closing-the-dialog-box.md)  
  
-   [销毁对话框](../mfc/destroying-the-dialog-box.md)  
  
-   [对话框数据交换 \(DDX\) 和验证 \(DDV\)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [属性表对话框](../mfc/property-sheets-and-property-pages-mfc.md)  
  
## 请参阅  
 [对话框](../mfc/dialog-boxes.md)