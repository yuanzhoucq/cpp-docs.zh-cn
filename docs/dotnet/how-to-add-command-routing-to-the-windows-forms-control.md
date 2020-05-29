---
title: 如何：向 Windows 窗体控件添加命令传送
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: ad64a12051c22a0cfca99d3ec9c5abef579902f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365173"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>如何：向 Windows 窗体控件添加命令传送

[CWinFormsView](../mfc/reference/cwinformsview-class.md)将命令和更新命令 UI 消息路由到用户控件，以允许它处理 MFC 命令（例如，框架菜单项和工具栏按钮）。

用户控件使用[ICommandTarget：：初始化](../mfc/reference/icommandtarget-interface.md#initialize)来存储对 命令源对象的引用`m_CmdSrc`，如以下示例所示。 要使用`ICommandTarget`，必须添加对 mfcmifc80.dll 的引用。

`CWinFormsView`通过将多个常见的 MFC 视图通知转发到托管用户控件来处理它们。 这些通知包括["初始更新](../mfc/reference/iview-interface.md#oninitialupdate)["、"更新"](../mfc/reference/iview-interface.md#onupdate)和["激活视图"](../mfc/reference/iview-interface.md#onactivateview)方法。

本主题假定您以前已完成[了"如何操作：在对话框中创建用户控制和主机](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)["以及如何：创建用户控制和主机 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。

### <a name="to-create-the-mfc-host-application"></a>创建 MFC 主机应用程序

1. 打开您在"如何操作"中创建的 Windows 窗体控件库[：在对话框中创建用户控件和主机](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。

1. 添加对 mfcmifc80.dll 的引用，您可以通过右键单击**解决方案资源管理器**中的项目节点，选择 **"添加**"，**参考**，然后浏览到 Microsoft Visual Studio 10.0_VC_atlmfc_lib。

1. 打开UserControl1.Designer.cs并添加以下使用语句：

    ```
    using Microsoft.VisualC.MFC;
    ```

1. 此外，在UserControl1.Designer.cs中，更改此行：

    ```
    partial class UserControl1
    ```

   更改为：

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. 将其添加为`UserControl1`的类定义的第一行：

    ```
    private ICommandSource m_CmdSrc;
    ```

1. 将以下方法定义添加到`UserControl1`（我们将在下一步中创建 MFC 控件的 ID）：

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

1. 打开您在["如何创建"中的 MFC 应用程序：创建用户控制和主机 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。

1. 添加将调用`singleMenuHandler`的菜单选项。

   转到**资源视图**（Ctrl_Shift_E），展开**菜单**文件夹，然后双击**IDR_MFC02TYPE**。 这将显示菜单编辑器。

   在 **"视图"** 菜单底部添加菜单选项。 请注意"**属性"** 窗口中菜单选项的 ID。 保存文件。

   在**解决方案资源管理器**中，打开 Resource.h 文件，复制刚刚添加的菜单选项的 ID 值，并将该值作为第一个参数`m_CmdSrc.AddCommandHandler`粘贴到 C# 项目方法`Initialize`中的调用（`32771`如有必要替换）。

1. 生成并运行该项目。

   在“生成”**** 菜单中，单击“生成解决方案”****。

   在 **"调试"** 菜单上，单击"**不调试即可开始**"。

   选择您添加的菜单选项。 请注意，调用 .dll 中的方法。

## <a name="see-also"></a>另请参阅

[以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[ICommandSource 接口](../mfc/reference/icommandsource-interface.md)<br/>
[ICommandTarget 接口](../mfc/reference/icommandtarget-interface.md)
