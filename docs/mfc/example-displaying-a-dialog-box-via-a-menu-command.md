---
title: 示例：通过菜单命令显示对话框
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
ms.openlocfilehash: 830ba27945ce8da2abd52c7f29d786d098113151
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483481"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>示例：通过菜单命令显示对话框

本主题包含到过程：

- 显示模式对话框通过菜单命令。

- 显示无模式对话框通过菜单命令。

这两个示例过程是 MFC 应用程序，将使用创建的应用程序中工作[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)。

过程使用以下名称和值：

|项|名称或值|
|----------|-------------------|
|应用程序|DisplayDialog|
|菜单命令|视图菜单; 上的命令进行测试命令 ID = ID_VIEW_TEST|
|对话框|测试对话框;类 = CTestDialog;标头文件 = TestDialog.h;变量 = testdlg，ptestdlg|
|命令处理程序|OnViewTest|

### <a name="to-display-a-modal-dialog-box"></a>若要显示模式对话框

1. 创建菜单命令;请参阅[创建菜单或菜单项](../windows/creating-a-menu.md)。

1. 创建对话框;请参阅[启动对话框编辑器](../windows/creating-a-new-dialog-box.md)。

1. 添加对话框中的类。 请参阅[添加类](../ide/adding-a-class-visual-cpp.md)有关详细信息。

1. 在中**类视图**，选择文档类 (CDisplayDialogDoc)。 在 **“属性”** 窗口中，单击 **“事件”** 按钮。 双击的左窗格中的菜单命令 (ID_VIEW_TEST) 的 ID**属性**窗口，然后选择**命令**。 在右窗格中，单击向下箭头，然后选择**\<添加 > OnViewTest**。

   如果与大型机的 MDI 应用程序添加菜单命令，请改为选择应用程序类 (CDisplayDialogApp)。

1. 将以下 include 语句 CDisplayDialogDoc.cpp （或 CDisplayDialogApp.cpp） 添加现有包含语句之后：

   [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]

1. 将以下代码添加到`OnViewTest`来实现该函数：

   [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]

### <a name="to-display-a-modeless-dialog-box"></a>若要显示无模式对话框

1. 执行前四个步骤，以显示模式对话框中，但在步骤 4 中选择的视图类 (CDisplayDialogView)。

1. 编辑 DisplayDialogView.h:

   - 声明声明前面的第一类的对话框类：

         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_3.h)]

   - 将指针声明为对话框的后的 public 节中的属性：

         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_4.h)]

1. 编辑 DisplayDialogView.cpp:

   - 添加以下 include 语句后现有 include 语句：

         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]

   - 将以下代码添加到构造函数：

         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]

   - 将以下代码添加到析构函数：

         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]

   - 将以下代码添加到`OnViewTest`来实现该函数：

         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[模式和无模式对话框](../mfc/modal-and-modeless-dialog-boxes.md)
