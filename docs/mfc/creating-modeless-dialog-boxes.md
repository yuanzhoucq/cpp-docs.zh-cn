---
title: "创建无模式对话框 | Microsoft Docs"
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
  - "MFC 对话框, 无模式"
  - "无模式对话框, 创建"
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建无模式对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于无模式对话框，必须提供自己在对话框类的公共构造函数。  创建无模式对话框，请告诉公共构造函数然后调用对话框对象的成员函数 [创建](../Topic/CDialog::Create.md) 对话框资源加载。  在构造函数调用过程中，您可以在调用 **创建** 或。  如果对话框资源具有属性 **WS\_VISIBLE**对话框，立即显示。  否则，必须调用成员函数。[ShowWindow](../Topic/CWnd::ShowWindow.md)  
  
## 请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)