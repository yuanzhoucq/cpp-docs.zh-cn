---
title: "框架中的对话框组件 | Microsoft Docs"
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
  - "对话框类, 对话框组件"
  - "对话框模板, MFC 框架"
  - "MFC 对话框, 关于 MFC 对话框"
  - "MFC 对话框, 创建"
  - "MFC 对话框, 对话框资源"
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 框架中的对话框组件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 框架，对话框有两个组件：  
  
-   指定对话框的控件及其位置的对话框模板资源。  
  
     对话框资源存储窗口创建对话框窗口和显示该对话框的模板。  模板指定对话框的特性，其中包括其大小、位置、样式和对话框控件的类型和位置。  您通常使用作为资源存储的对话框模板，但您也可以创建自己内存中的模板。  
  
-   对话框类，从中派生对话框，[CDialog](../mfc/reference/cdialog-class.md)用于管理提供编程接口。  
  
     对话框是窗口，然后附加到窗口时，窗口显示。  当对话框创建窗口时，对话框模板资源将用作模板用于创建子窗口控件的对话框。  
  
## 请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)