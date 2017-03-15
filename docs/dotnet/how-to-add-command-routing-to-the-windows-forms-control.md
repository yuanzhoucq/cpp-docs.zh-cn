---
title: "如何：向 Windows 窗体控件添加命令传送 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令传送 [c + +] 添加到 Windows 窗体控件"
  - "Windows 窗体控件 [c + +]，命令路由"
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：向 Windows 窗体控件添加命令传送
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CWinFormsView](../mfc/reference/cwinformsview-class.md) 将命令和更新命令 UI 消息路由到用户控件，以允许应用程序处理 MFC 命令 （例如，框架菜单项和工具栏按钮）。  
  
 用户控件使用 [ICommandTarget::Initialize](../Topic/ICommandTarget::Initialize.md) 来存储对中的命令源对象的引用 `m_CmdSrc`, ，如在下面的示例所示。 若要使用 `ICommandTarget` 必须添加对将 mfcmifc80.dll 的引用。  
  
 `CWinFormsView` 通过将它们转发到托管的用户控件来处理若干常见的 MFC 查看通知。 这些通知包括 [OnInitialUpdate](../Topic/IView::OnInitialUpdate.md), ，[OnUpdate](../Topic/IView::OnUpdate.md) 和 [OnActivateView](../Topic/IView::OnActivateView.md) 方法 [IView 接口](../mfc/reference/iview-interface.md)。  
  
 本主题假定您先前已完成 [如何︰ 在对话框中创建用户控件并承载](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) 和 [如何︰ 创建用户控件和 MDI 主机视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
### <a name="to-create-the-mfc-host-application"></a>若要创建 MFC 宿主应用程序  
  
1.  打开 Windows 窗体控件库中创建 [如何︰ 在对话框中创建用户控件并承载](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。  
  
2.  添加对将 mfcmifc80.dll，可以通过右键单击项目节点中的执行此操作的引用 **解决方案资源管理器**, ，选择 **添加**, ，**引用**, ，然后浏览到 Microsoft Visual Studio 10.0\VC\atlmfc\lib。  
  
3.  打开 UserControl1.Designer.cs 并添加以下 using 语句︰  
  
    ```  
    using Microsoft.VisualC.MFC;  
    ```  
  
4.  此外，在 UserControl1.Designer.cs，将此行更改︰  
  
    ```  
    partial class UserControl1  
    ```  
  
     为以下内容︰  
  
    ```  
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget  
    ```  
  
5.  将下行添加的类定义的第一行 `UserControl1`:  
  
    ```  
    private ICommandSource m_CmdSrc;  
    ```  
  
6.  添加以下方法定义为 `UserControl1` （我们将在下一步创建 MFC 控件的 ID）︰  
  
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
  
7.  打开你在中创建的 MFC 应用程序 [如何︰ 创建用户控件和 MDI 主机视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
8.  添加将调用一个菜单选项 `singleMenuHandler`。  
  
     转到 **资源视图** (Ctrl + Shift + E) 展开 **菜单** 文件夹，然后再双击 **IDR_MFC02TYPE**。 此时将显示菜单编辑器。  
  
     在底部添加一个菜单选项 **视图** 菜单。 请注意菜单选项中的 ID **属性** 窗口。 保存该文件。  
  
     在 **解决方案资源管理器**, 、 打开 Resource.h 文件，只需添加的菜单选项的 ID 值作为复制并粘贴该值的第一个参数 `m_CmdSrc.AddCommandHandler` 在 C# 项目中调用 `Initialize` 方法 (替换 `32771` 如有必要)。  
  
9. 生成并运行该项目。  
  
     在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
     在 **调试** 菜单上，单击 **启动而不调试**。  
  
     选择添加菜单选项。 请注意，调用.dll 文件中的方法。  
  
## <a name="see-also"></a>另请参阅  
 [作为 MFC 视图承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [ICommandSource 接口](../mfc/reference/icommandsource-interface.md)   
 [ICommandTarget 接口](../mfc/reference/icommandtarget-interface.md)   
 [CommandHandler](../Topic/CommandHandler%20Delegate.md)