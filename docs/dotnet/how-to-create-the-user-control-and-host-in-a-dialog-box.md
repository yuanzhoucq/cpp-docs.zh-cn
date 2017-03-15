---
title: "如何：创建用户控件并将它承载在对话框中 | Microsoft Docs"
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
  - "MFC [C++], 承载 Windows 窗体控件"
  - "Windows 窗体 [C++], MFC 支持"
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：创建用户控件并将它承载在对话框中
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文中的步骤假设您正在创建一个基于对话框 \([CDialog Class](../mfc/reference/cdialog-class.md)\) 的 Microsoft Foundation Classes \(MFC\) 项目，但您还可以将对 Windows 窗体控件的支持添加到现有 MFC 对话框。  
  
### 创建 .NET 用户控件  
  
1.  创建名为 `WindowsFormsControlLibrary1` 的 Visual C\# Windows 窗体控件库项目。  
  
     在**“文件”**菜单上，单击**“新建”**，然后单击**“项目”**。  在**“Visual C\#”**文件夹中，选择**“Windows 窗体控件库”**。  
  
     通过单击**“确定”**，接受 `WindowsFormsControlLibrary1` 项目名称。  
  
     默认情况下，.NET 控件的名称将为 `UserControl1`。  
  
2.  向 `UserControl1` 添加子控件。  
  
     在**“工具箱”**中，打开**“所有 Windows 窗体”**列表。  将一个**“Button”**控件拖到 `UserControl1` 设计图面上。  
  
     再添加一个**“TextBox”**控件。  
  
3.  在**“解决方案资源管理器”**中，双击**“UserControl1.Designer.cs”**以打开它进行编辑。  将 TextBox 和 Button 的声明从 `private` 更改为 `public`。  
  
4.  生成项目。  
  
     在**“生成”**菜单上，单击**“生成解决方案”**。  
  
### 创建 MFC 宿主应用程序  
  
1.  创建 MFC 应用程序项目。  
  
     在**“文件”**菜单上，单击**“新建”**，然后单击**“项目”**。  在**“Visual C\+\+”**文件夹中，选择**“MFC 应用程序”**。  
  
     在**“名称”**框中键入 `MFC01`。  将解决方案的设置更改为**“添入解决方案”**。  单击**“确定”**。  
  
     在**“MFC 应用程序向导”**中，为应用程序类型选择**“基于对话框的”**。  接受剩余的默认设置并单击**“完成”**。  这将创建具有 MFC 对话框的 MFC 应用程序。  
  
2.  向 MFC 对话框添加 placeholder 控件。  
  
     在**“视图”**菜单上，单击**“资源视图”**。  在**“资源视图”**中，展开**“对话框”**文件夹，并双击 `IDD_MFC01_DIALOG`。  对话框资源将显示在**“资源编辑器”**中。  
  
     在**“工具箱”**中，打开**“对话框编辑器”**列表。  将**“静态文本”**控件拖到对话框资源中。  **“静态文本”**控件将作为 .NET Windows 窗体控件的占位符使用。  重新调整其大小，使其大小接近 Windows 窗体控件大小。  
  
     在**“属性”**窗口中，将**“静态文本”**控件的**“ID”**更改为 `IDC_CTRL1`，将**“TabStop”**属性更改为**“True”**。  
  
3.  配置项目以获得公共语言运行时 \(CLR\) 支持。  
  
     在**“解决方案资源管理器”**中，右击 MFC01 项目节点，再单击**“属性”**。  
  
     在**“属性页”**对话框中的**“配置属性”**下选择**“常规”**。  在“项目默认值”部分中，将“公共语言运行时支持”设置为“公共语言运行时支持 \(\/clr\)”。  
  
     在**“配置属性”**下面，展开**“C\/C\+\+”**，然后选择**“常规”**节点。  将**“调试信息格式”**设置为**“程序数据库\(\/Zi\)”**。  
  
     选择**“代码生成”**节点。  将**“启用最小重新生成”**设置为**“否\(\/Gm\-\)”**。  另外，将**“基本运行时检查”**设置为**“默认”**。  
  
     单击**“确定”**应用更改。  
  
4.  向 .NET 控件添加引用。  
  
     在“解决方案资源管理器”中，右击 MFC01 项目节点，再单击“添加”、“引用”。  在**“属性页”**上，单击**“添加新引用”**，选择**“WindowsFormsControlLibrary1”**（在**“项目”**选项卡下），然后单击**“确定”**。  此操作添加一个 [\/FU](../build/reference/fu-name-forced-hash-using-file.md) 编译器选项形式的引用，以便程序进行编译。  它还将 WindowsFormsControlLibrary1.dll 的副本放入 \\MFC01\\ 项目文件夹中，以便程序运行。  
  
5.  在 Stdafx.h 中，请找到以下行：  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     在此行上面添加以下行：  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  添加代码以创建托管控件。  
  
     首先，声明托管控件。  在 MFC01Dlg.h 中，转到对话框类的声明，并添加受保护范围内的用户控件的数据成员，如下所示。  
  
    ```  
    class CMFC01Dlg : public CDialog  
    {  
       // ...  
       // Data member for the .NET User Control:  
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;  
    ```  
  
     接下来，提供托管控件的实现。  在 MFC01Dlg.cpp 中，在 MFC 应用程序向导生成的 `CMFC01Dlg::DoDataExchange`（而不是相同文件中的 `CAboutDlg::DoDataExchange`）的对话框重写中，添加下列代码以创建托管控件并将其与静态占位符 IDC\_CTRL1 相关联。  
  
    ```  
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
    {  
       CDialog::DoDataExchange(pDX);  
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);  
    }  
    ```  
  
7.  生成并运行该项目。  
  
     在“解决方案资源管理器”中，右击“MFC01”，再单击“设为启动项目”。  
  
     在**“生成”**菜单上，单击**“生成解决方案”**。  
  
     在**“调试”**菜单上，单击**“开始执行\(不调试\)”**。  MFC 对话框应该显示 Windows 窗体控件。  
  
## 请参阅  
 [在 MFC 对话框中承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)