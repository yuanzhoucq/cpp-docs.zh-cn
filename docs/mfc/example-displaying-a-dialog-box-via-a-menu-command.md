---
title: 示例：通过菜单命令显示对话框
ms.date: 09/07/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
ms.openlocfilehash: ec4e0495519db3e30213d8abb9292409f2110e3c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078828"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>示例：通过菜单命令显示对话框

本主题包含以下过程：

- 通过菜单命令显示模式对话框。

- 通过菜单命令显示无模式对话框。

这两个示例过程都适用于 MFC 应用程序，并可在使用[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)创建的应用程序中使用。

这些过程使用以下名称和值：

|Item|名称或值|
|----------|-------------------|
|应用程序|DisplayDialog|
|菜单命令|"视图" 菜单上的测试命令;命令 ID = ID_VIEW_TEST|
|对话框|"测试" 对话框;类 = CTestDialog;头文件 = TestDialog;Variable = testdlg，ptestdlg|
|命令处理程序|OnViewTest|

### <a name="to-display-a-modal-dialog-box"></a>显示模式对话框

1. 创建菜单命令;请参阅[创建菜单或菜单项](../windows/creating-a-menu.md)。

1. 创建对话框;请参阅[启动对话框编辑器](../windows/creating-a-new-dialog-box.md)。

1. 为您的对话框添加一个类。 有关详细信息，请参阅[添加类](../ide/adding-a-class-visual-cpp.md)。

1. 在**类视图**中，选择 "文档类" （CDisplayDialogDoc）。 在“属性”窗口中，单击“事件”按钮。 双击菜单命令的 ID （ID_VIEW_TEST）。 接下来，单击向下箭头，然后选择 **\<添加 > OnViewTest**。

   如果已将菜单命令添加到 MDI 应用程序的大型机，请改为选择应用程序类（CDisplayDialogApp）。

1. 将以下 include 语句添加到 CDisplayDialogDoc （或 CDisplayDialogApp）中的现有 include 语句之后：

   ```cpp
   #include "TestDialog.h"
   ```

1. 将以下代码添加到 `OnViewTest` 以实现函数：

   ```cpp
   CTestDialog testdlg;
   testdlg.DoModal();
   ```

### <a name="to-display-a-modeless-dialog-box"></a>显示无模式对话框

1. 执行前四个步骤以显示模式对话框，只不过在步骤4中选择视图类（CDisplayDialogView）。

1. 编辑 DisplayDialogView：

   - 在第一个类声明之前声明对话框类：

   ```cpp
   class CTestDialog;
   ```

   - 声明一个指向对话框的指针，并在 public 节后：

   ```cpp
   CTestDialog* m_pTestDlg;
   ```

1. 编辑 DisplayDialogView：

   - 将以下 include 语句添加到现有 include 语句之后：

   ```cpp
   #include "TestDialog.h"
   ```

   - 将以下代码添加到构造函数：

   ```cpp
   m_pTestDlg = NULL;
   ```

   - 将以下代码添加到析构函数：

   ```cpp
   delete m_pTestDlg;
   ```

   - 将以下代码添加到 `OnViewTest` 以实现函数：

   ```cpp
   if (NULL == m_pTestDlg)
   {
      m_pTestDlg = new CTestDialog(this);
      m_pTestDlg->Create(CTestDialog::IDD, this);
   }
   m_pTestDlg->ShowWindow(SW_SHOW);
   ```

## <a name="see-also"></a>另请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[模式和无模式对话框](../mfc/modal-and-modeless-dialog-boxes.md)
