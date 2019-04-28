---
title: 如何：添加命令路由到 Windows 窗体控件
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: 8f633cf744314833409a3ffeacf8c850429e099c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222905"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>如何：添加命令路由到 Windows 窗体控件

[CWinFormsView](../mfc/reference/cwinformsview-class.md)将命令和更新命令 UI 消息路由到用户控件，使其能够处理 MFC 命令 （例如，框架菜单项和工具栏按钮）。

使用用户控件[ICommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize)用于存储对命令源对象中的引用`m_CmdSrc`，如以下示例所示。 若要使用`ICommandTarget`必须添加对 mfcmifc80.dll 的引用。

`CWinFormsView` 处理多个常见的 MFC 视图通知转发给托管的用户控件。 这些通知包括[OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate)， [OnUpdate](../mfc/reference/iview-interface.md#onupdate)并[OnActivateView](../mfc/reference/iview-interface.md#onactivateview)方法。

本主题假定你之前已完成[如何：在对话框中创建用户控件并承载](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)和[如何：创建用户控件并承载 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。

### <a name="to-create-the-mfc-host-application"></a>若要创建 MFC 宿主应用程序

1. 打开 Windows 窗体控件库中创建[如何：在对话框中创建用户控件并承载](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。

1. 添加对 mfcmifc80.dll，可以通过右键单击项目节点中的执行此操作的引用**解决方案资源管理器**，选择**添加**，**引用**，然后浏览到Microsoft Visual Studio 10.0\VC\atlmfc\lib。

1. 打开 UserControl1.Designer.cs 并添加以下 using 语句：

    ```
    using Microsoft.VisualC.MFC;
    ```

1. 此外，在 UserControl1.Designer.cs 中更改此行：

    ```
    partial class UserControl1
    ```

   更改为：

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. 将下行添加的类定义的第一行`UserControl1`:

    ```
    private ICommandSource m_CmdSrc;
    ```

1. 添加以下方法定义为`UserControl1`（我们将在下一步中创建 MFC 控件的 ID）：

    ```
    public void Initialize (ICommandSource cmdSrc)
    {
       m_CmdSrc = cmdSrc;
       // need ID of control in MFC dialog and callback function
       m_CmdSrc.AddCommandHandler(32771, new CommandHandler (singleMenuHandler));
    }

    private void singleMenuHandler (uint cmdUI)
    {
       // User command handler code
       System.Windows.Forms.MessageBox.Show("Custom menu option was clicked.");
    }
    ```

1. 打开你在中创建的 MFC 应用程序[如何：创建用户控件并承载 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。

1. 添加将调用一个菜单选项`singleMenuHandler`。

   转到**资源视图**(Ctrl + Shift + E)，展开**菜单**文件夹，然后再双击**IDR_MFC02TYPE**。 这将显示在菜单编辑器。

   在底部添加一个菜单选项**视图**菜单。 请注意中的菜单选项的 ID**属性**窗口。 保存该文件。

   在中**解决方案资源管理器**、 打开 Resource.h 文件，复制刚添加的菜单选项的 ID 值并将该值粘贴到第一个参数`m_CmdSrc.AddCommandHandler`C# 项目中调用`Initialize`（替换方法`32771`如有必要)。

9. 生成并运行该项目。

   在 **“生成”** 菜单上，单击 **“生成解决方案”**。

   上**调试**菜单上，单击**启动但不调试**。

   选择添加菜单选项。 请注意，调用.dll 文件中的方法。

## <a name="see-also"></a>请参阅

[以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[ICommandSource 接口](../mfc/reference/icommandsource-interface.md)<br/>
[ICommandTarget 接口](../mfc/reference/icommandtarget-interface.md)
