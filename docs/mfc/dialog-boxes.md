---
title: "对话框 | Microsoft Docs"
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
  - "CDialog 类, MFC 对话框"
  - "MFC 对话框"
  - "MFC, 对话框"
  - "有模式对话框, MFC 对话框"
  - "无模式对话框, MFC 对话框"
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于窗口的应用程序。用户频繁通信通过对话框。  [CDialog](../mfc/reference/cdialog-class.md) 类用于管理的对话框提供一个界面，在 Visual C\+\+ 对话框编辑器使您可以轻松地设计对话框和创建自己的对话框模板资源，并且，代码向导来简化初始化和验证对话框中的控件的过程和收集用户输入的值。  
  
 包含对话框控件，包括：  
  
-   Windows 公共控件 \(编辑框、按钮、列表框、组合框、树控件、控件列表和进度指示器。  
  
-   ActiveX 控件。  
  
-   所有者描述的控件：您负责在对话框控件的绘图。  
  
 大多数对话框都是模式线程，需要用户在使用程序的其他任何部分之前关闭对话框。  但创建无模式对话框是可以的，允许用户使用其他窗口时，该对话框打开时。  MFC 支持具有两类对话框的 `CDialog`。  使用对话框模板资源，控件排列和管理类型，创建带有 [对话框编辑器](../mfc/dialog-editor.md)。  
  
 [属性表](../mfc/property-sheets-mfc.md)，也称为对话框选项卡，是包含“页”的不同对话框控件的对话框。  每个页面都具有一个文件夹“选项卡”顶部。  单击选项卡将对话框的前面将该页。  
  
## 您想进一步了解什么？  
  
-   [示例：显示对话框通过菜单命令](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)  
  
-   [框架中的对话框组件](../mfc/dialog-box-components-in-the-framework.md)  
  
-   [模式和无模式对话框](../mfc/modal-and-modeless-dialog-boxes.md)  
  
-   对话框中的[属性表和属性页](../mfc/property-sheets-and-property-pages-mfc.md)  
  
-   [创建对话框资源](../mfc/creating-the-dialog-resource.md)  
  
-   [创建带有代码向导的对话框类](../mfc/creating-a-dialog-class-with-code-wizards.md)  
  
-   [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)  
  
-   [对话框数据交换 \(DDX\) 和验证 \(DDV\)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [对控件类型的安全访问对话框中](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [映射到类的窗口消息](../mfc/mapping-windows-messages-to-your-class.md)  
  
-   [经常重写的成员函数](../mfc/commonly-overridden-member-functions.md)  
  
-   [通常添加的成员函数](../mfc/commonly-added-member-functions.md)  
  
-   [通用对话框类](../mfc/common-dialog-classes.md)  
  
-   [在 OLE 的对话框](../mfc/dialog-boxes-in-ole.md)  
  
-   创建用户界面是对话框的应用程序：参见 [CMNCTRL1](../top/visual-cpp-samples.md) 或 [CMNCTRL2](../top/visual-cpp-samples.md) 示例程序。  应用程序向导提供此选项。  
  
-   [示例](../mfc/dialog-sample-list.md)  
  
## 请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)