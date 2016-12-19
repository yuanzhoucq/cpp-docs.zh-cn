---
title: "示例：通过菜单命令显示对话框 | Microsoft Docs"
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
  - "对话框, MFC"
  - "示例 [MFC], 对话框"
  - "菜单项, 示例"
  - "MFC 对话框, 显示"
  - "MFC 对话框, 示例"
  - "有模式对话框, 显示"
  - "无模式对话框, 显示"
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 示例：通过菜单命令显示对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题包含过程：  
  
-   通过菜单命令显示模式对话框。  
  
-   通过菜单命令显示无模式对话框。  
  
 两个示例过程适用于 MFC 应用程序工作，并在与 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)创建的应用程序。  
  
 过程使用以下名称和值：  
  
|项|名称或值|  
|-------|----------|  
|Application|DisplayDialog|  
|菜单命令|在"视图"菜单上的命令；测试\= ID\_VIEW\_TEST 命令 ID|  
|对话框|测试对话框；类为 CTestDialog;头文件 TestDialog.h 为；变量 testdlg \=，ptestdlg|  
|命令处理程序|OnViewTest|  
  
### 显示模式对话框  
  
1.  创建菜单命令；参见 [创建菜单或菜单项](../windows/creating-a-menu.md)。  
  
2.  创建对话框；参见 [启动对话框编辑器](../mfc/creating-a-new-dialog-box.md)。  
  
3.  添加对话框的类。  参见 [添加类](../ide/adding-a-class-visual-cpp.md)。更多信息。  
  
4.  在 **类视图**中，选择文档 CDisplayDialogDoc 类 \(\)。  在 **属性** 窗口，单击 **事件** 按钮。  双击菜单命令 \(ID\_VIEW\_TEST\) 的 ID。**属性** 窗口并选择 **命令**的左窗格。  在右窗格中，单击下箭头然后选择 **\<Add OnViewTest\>** 。  
  
     如果已添加菜单命令向 MDI 应用程序的主框架中，选择应用程序类 \(CDisplayDialogApp\)。  
  
5.  添加下列包括语句添加到 CDisplayDialogDoc.cpp \(或\) 在 CDisplayDialogApp.cpp 存在之后包括语句：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
6.  添加以下代码以实现 `OnViewTest` 函数：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]  
  
### 显示无模式对话框  
  
1.  执行最后四个步骤显示模式对话框，因此，除非选择视图类 \(\) CDisplayDialogView 在步骤 4。  
  
2.  编辑 DisplayDialogView.h:  
  
    -   类声明前面声明的对话框类：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_3.h)]  
  
    -   中声明指针到对话框，即使特性 public 节之后：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_4.h)]  
  
3.  编辑 DisplayDialogView.cpp:  
  
    -   在存在之后添加下列包括语句包括语句：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
    -   将下面的代码添加到构造函数：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]  
  
    -   添加下列代码。析构函数：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]  
  
    -   添加以下代码以实现 `OnViewTest` 函数：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]  
  
 并且，请参见下面的知识库文章：  
  
-   Q251059:如何：提供自己的窗口类名。MFC 对话框  
  
## 请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [模式和无模式对话框](../mfc/modal-and-modeless-dialog-boxes.md)