---
title: "初始化对话框 | Microsoft Docs"
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
  - "初始化对话框"
  - "MFC 对话框, 初始化"
  - "有模式对话框, 初始化"
  - "无模式对话框, 初始化"
  - "OnInitDialog 方法"
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 初始化对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在对话框和及其所有控件后创建，但是，在对话框 \(任何类型\) 之前出现在屏幕上，对话框对象的 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) 成员函数调用。  在调用 `DoModal` 期间，对于模式对话框，这发生。  对于无模式对话框，因此，在调用 **创建** 时，调用 `OnInitDialog`。  通常可以重写 `OnInitDialog` 初始化对话框的控件，例如设置编辑框的初始文本。  必须调用基类，`CDialog`的 `OnInitDialog` 成员函数中，从 `OnInitDialog` 重写。  
  
 如果希望对话框设置的背景色。与在应用程序中其他所有对话框\)，请参见 [将对话框的背景色](../mfc/setting-the-dialog-box’s-background-color.md)。  
  
## 请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)