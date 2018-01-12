---
title: "如何： 添加命令路由到 Windows 窗体控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bcd082b22c61e2444d70d936c225e538c2429222
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>如何：向 Windows 窗体控件添加命令传送
[CWinFormsView](../mfc/reference/cwinformsview-class.md)将命令和更新命令 UI 消息路由到用户控件，以允许其处理 MFC 命令 （例如，帧菜单项和工具栏按钮）。  
  
 该用户控件使用[ICommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize)来存储对中的命令源对象的引用`m_CmdSrc`，下面的示例中所示。 若要使用`ICommandTarget`必须添加对 mfcmifc80.dll 的引用。  
  
 `CWinFormsView`通过将它们转发到托管的用户控件中处理多个常见的 MFC 视图通知。 这些通知包括[OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate)， [OnUpdate](../mfc/reference/iview-interface.md#onupdate)和[OnActivateView](../mfc/reference/iview-interface.md#onactivateview)方法。  
  
 本主题假定你以前已完成[如何： 在对话框中创建用户控件并承载](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)和[如何： 创建用户控件和主机 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
### <a name="to-create-the-mfc-host-application"></a>若要创建 MFC 主机应用程序  
  
1.  打开 Windows 窗体控件库中创建[如何： 在对话框中创建用户控件并承载](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。  
  
2.  添加对 mfcmifc80.dll，你可以通过右键单击中的项目节点中执行此操作的引用**解决方案资源管理器**，选择**添加**，**引用**，然后浏览到Microsoft Visual Studio 10.0\VC\atlmfc\lib。  
  
3.  打开 UserControl1.Designer.cs 并添加以下 using 语句：  
  
    ```  
    using Microsoft.VisualC.MFC;  
    ```  
  
4.  此外，在 UserControl1.Designer.cs，将更改以下行：  
  
    ```  
    partial class UserControl1  
    ```  
  
     更改为：  
  
    ```  
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget  
    ```  
  
5.  添加为的类定义的第一行`UserControl1`:  
  
    ```  
    private ICommandSource m_CmdSrc;  
    ```  
  
6.  添加以下方法定义到`UserControl1`（我们将在下一步中创建 MFC 控件的 ID）：  
  
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
  
7.  打开你在中创建的 MFC 应用程序[如何： 创建用户控件和主机 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
8.  添加菜单选项，将会调用`singleMenuHandler`。  
  
     转到**资源视图**(Ctrl + Shift + E) 展开**菜单**文件夹，然后再双击**IDR_MFC02TYPE**。 此时将显示菜单编辑器。  
  
     添加在底部的菜单选项**视图**菜单。 请注意中的菜单选项的 ID**属性**窗口。 保存该文件。  
  
     在**解决方案资源管理器**打开 Resource.h 文件，复制刚添加的菜单选项的 ID 值并将该值粘贴到的第一个参数`m_CmdSrc.AddCommandHandler`C# 项目中调用`Initialize`方法 （使用替换`32771`如有必要)。  
  
9. 生成并运行该项目。  
  
     在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
     上**调试**菜单上，单击**启动而不调试**。  
  
     选择添加菜单选项。 请注意，调用.dll 文件中的方法。  
  
## <a name="see-also"></a>请参阅  
 [作为 MFC 视图承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [ICommandSource 接口](../mfc/reference/icommandsource-interface.md)   
 [ICommandTarget 接口](../mfc/reference/icommandtarget-interface.md)   
 [CommandHandler](http://msdn.microsoft.com/Library/22096734-e074-4aca-8523-4b15590109f9)