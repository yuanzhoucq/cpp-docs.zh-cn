---
title: 示例： 显示一个对话框，通过菜单命令 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20d355215388861a7bc2586c2c253cd551124809
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347982"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>示例：通过菜单命令显示对话框
本主题包含的过程，以：  
  
-   显示模式对话框，通过菜单命令。  
  
-   显示无模式对话框，可通过菜单命令。  
  
 这两个示例过程适用于 MFC 应用程序，并将在你创建与应用程序中工作[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)。  
  
 过程使用以下名称和值：  
  
|项|名称或值|  
|----------|-------------------|  
|应用程序|DisplayDialog|  
|菜单命令|测试视图菜单; 上的命令命令 ID = ID_VIEW_TEST|  
|对话框|测试对话框;类 = CTestDialog;标头文件 = TestDialog.h;变量 = testdlg，ptestdlg|  
|命令处理程序|OnViewTest|  
  
### <a name="to-display-a-modal-dialog-box"></a>若要显示模式对话框  
  
1.  创建菜单命令中;请参阅[创建菜单或菜单项](../windows/creating-a-menu.md)。  
  
2.  创建对话框;请参阅[启动对话框编辑器](../windows/creating-a-new-dialog-box.md)。  
  
3.  添加对话框中的类。 请参阅[添加类](../ide/adding-a-class-visual-cpp.md)有关详细信息。  
  
4.  在**类视图**，选择文档类 (CDisplayDialogDoc)。 在 **“属性”** 窗口中，单击 **“事件”** 按钮。 双击的 ID 中的左窗格中的菜单命令 (ID_VIEW_TEST)**属性**窗口，然后选择**命令**。 在右窗格中，单击向下箭头，然后选择**\<添加 > OnViewTest**。  
  
     如果将菜单命令添加到 MDI 应用程序的主机，请改为选择应用程序类 (CDisplayDialogApp)。  
  
5.  将以下 include 语句 CDisplayDialogDoc.cpp （或 CDisplayDialogApp.cpp） 添加现有包括语句后：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
6.  以下代码添加到`OnViewTest`来实现函数：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]  
  
### <a name="to-display-a-modeless-dialog-box"></a>若要显示无模式对话框  
  
1.  执行前四个步骤以显示一个模式对话框中，但在步骤 4 中选择视图类 (CDisplayDialogView)。  
  
2.  编辑 DisplayDialogView.h:  
  
    -   声明声明前面的第一类对话框类：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_3.h)]  
  
    -   属性的公共部分之后声明指向对话框中：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_4.h)]  
  
3.  编辑 DisplayDialogView.cpp:  
  
    -   添加以下 include 语句后现有 include 语句：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
    -   将以下代码添加到构造函数：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]  
  
    -   将以下代码添加到析构函数：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]  
  
    -   以下代码添加到`OnViewTest`来实现函数：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]  
  
 另请参阅以下知识库文章：  
  
-   Q251059： 如何： 提供 MFC 对话框自己窗口类名称  
  
## <a name="see-also"></a>请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [模式和无模式对话框](../mfc/modal-and-modeless-dialog-boxes.md)

