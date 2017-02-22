---
title: "Adding Event Handlers for Dialog Box Controls | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Dialog editor, adding event handlers to controls"
  - "controls [C++], event handlers"
  - "dialog box controls, events"
  - "event handlers, for dialog box controls"
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Adding Event Handlers for Dialog Box Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于已与某个类关联的项目对话框，在创建事件处理程序时可以利用某些快捷方式。  可以为默认控件通知事件或任何适用的 Windows 消息快速创建处理程序。  
  
#### 为默认控件通知事件创建处理程序  
  
1.  双击控件。  文本编辑器打开。  
  
2.  在文本编辑器中添加控件通知处理程序代码。  
  
#### 为任何适用的 Windows 消息创建处理程序  
  
1.  单击要为其处理通知事件的控件。  
  
2.  在[“属性”窗口](../Topic/Properties%20Window.md)中，单击“控件事件”按钮以显示与控件关联的普通 Windows 事件列表。  例如，**“关于”**对话框上的标准**“确定”**按钮列出下列通知事件：  
  
     **BN\_CLICKED**  
  
     **BN\_DOUBLECLICKED**  
  
     **BN\_KILLFOCUS**  
  
     **BN\_SETFOCUS**  
  
    > [!NOTE]
    >  或者，也可以选择对话框并单击**“控件事件”**按钮以显示对话框中所有控件的公共 Windows 事件列表。  
  
3.  在**“属性”**窗口中，单击要处理的事件右边的列，然后选择建议的通知事件名（例如，**OnBnClickedOK** 处理 **BN\_CLICKED**）。  
  
    > [!NOTE]
    >  或者，也可以提供您自己选择的事件处理程序名，而不是选择默认的事件处理程序名。  
  
     选择了事件后，Visual Studio 将打开文本编辑器并显示事件处理程序的代码。  例如，为默认 **OnBnClickedOK** 添加以下代码：  
  
    ```  
    void CAboutDlg::OnBnClickedOk(void)  
    {  
       // TODO: Add your control notification handler code here  
    }  
    ```  
  
 若要将事件处理程序添加到实现对话框的类以外的类，请使用[“事件处理程序向导”](../ide/event-handler-wizard.md)。  有关更多信息，请参见[添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 要求  
 Win32  
  
## 请参阅  
 [Default Control Events](../mfc/default-control-events.md)   
 [Defining Member Variables for Dialog Controls](../mfc/defining-member-variables-for-dialog-controls.md)   
 [对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)   
 [添加类](../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)