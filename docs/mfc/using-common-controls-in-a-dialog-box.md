---
title: "在对话框中使用公共控件 | Microsoft Docs"
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
  - "公共控件 [C++], 在对话框中"
  - "对话框控件 [C++], 公共控件"
  - "Windows 公共控件 [C++], 在对话框中"
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在对话框中使用公共控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Windows 公共控件可在 [对话框](../mfc/dialog-boxes.md)、窗体视图、记录视图和基于对话框模板的其他窗口中使用。  如下有微小变化的过程，对窗体仍有效。  
  
## 过程  
  
#### 在对话框中使用普通控件。  
  
1.  将控件放置在对话框模板 [使用对话框编辑器](../mfc/using-the-dialog-editor-to-add-controls.md)。  
  
2.  向对话框类添加表示控件的成员变量。  在 **添加成员变量** 对话框中，检查 **控件变量 \(O\)** 并确保 **控件**选择**类别**。  
  
3.  如果此公共控件提供输入到程序，声明在对话框类中的其他成员变量处理某些输入值。  
  
    > [!NOTE]
    >  在类视图中可以使用上下文菜单添加成员变量\(参见 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)\)。  
  
4.  在对话框类 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)中，为公共控件设置起始条件。  使用变量在上一步中创建，使用成员函数设置原始值和其他设置。  有关设置的详细信息参见控件的下面说明。  
  
     还可以使用 [对话框数据交换](../mfc/dialog-data-exchange-and-validation.md) \(DDX\) 初始化在对话框的控件。  
  
5.  在该控件的处理程序对话框中，使用成员变量来操作控件。  有关方法的详细信息参见控件的下面说明。  
  
    > [!NOTE]
    >  只是在对话框自身存在时，成员变量将存在。  在对话框关闭后，无法查询输入值的控件。  对来自普通控件的输入值有效，在对话框类中重写 `OnOK`。  在重写中，将查询输入值的控件并存储在对话框类的成员变量值。  
  
    > [!NOTE]
    >  对话框中，您还可以使用对话框数据交换设置或检索来自控件的值。  
  
## 备注  
 添加常见控件到对话框会导致对话框不再工作。  有关处理此情况的更多信息，参考 [Adding Controls to a Dialog Causes the Dialog to No Longer Function](../mfc/adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function.md)。  
  
## 你希望做什么？  
  
-   [手动向对话框添加控件代替使用对话框编辑器](../mfc/adding-controls-by-hand.md)  
  
-   [从一个标准 Windows 公共控件派生我的控件](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [将公共控件用作子窗口](../mfc/using-a-common-control-as-a-child-window.md)  
  
-   [接收来自控件的通知消息](../mfc/receiving-notification-from-common-controls.md)  
  
-   [对话框数据交换 \(DDX\)](../mfc/dialog-data-exchange-and-validation.md)  
  
## 请参阅  
 [创建和使用控件](../mfc/making-and-using-controls.md)   
 [控件](../mfc/controls-mfc.md)