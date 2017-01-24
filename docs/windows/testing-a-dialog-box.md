---
title: "Testing a Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Test Dialog command"
  - "testing, dialog boxes"
  - "dialog boxes, testing"
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Testing a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当您设计对话框时，无需编译程序即可模拟并测试其运行时行为。 在此模式中，您可以：  
  
-   键入文本、从组合框列表中选择、打开或关闭选项，以及选择命令。  
  
-   测试 Tab 键顺序。  
  
-   测试控件的分组，如单选按钮和复选框。  
  
-   在对话框中测试控件的键盘快捷键。  
  
    > [!NOTE]
    >  与使用向导生成的对话框代码的连接不包括在此模拟中。  
  
 当测试对话框时，它通常显示在与主程序窗口相对的位置。 如果已经将对话框的 Absolute Align 属性设置为 True，则对话框显示在相对于屏幕左上角的位置。  
  
### 测试对话框  
  
1.  当对话框编辑器为活动窗口时，在菜单栏上，选择**“格式”**、**“测试对话框”**。  
  
2.  若要结束此模拟，请按 Esc，或选择正在测试的对话框中的**“关闭”**按钮。  
  
 有关如何向托管项目中添加资源的信息，请参阅 [桌面应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [Dialog Editor](../mfc/dialog-editor.md)   
 [显示或隐藏对话框编辑器工具栏](../mfc/showing-or-hiding-the-dialog-editor-toolbar.md)