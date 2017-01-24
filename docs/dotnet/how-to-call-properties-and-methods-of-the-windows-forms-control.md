---
title: "如何：调用 Windows 窗体控件的属性和方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "调用方法, Windows 窗体控件"
  - "调用属性"
  - "调用属性, Windows 窗体控件"
  - "方法调用, Windows 窗体"
  - "Windows 窗体控件 [C++], 方法"
  - "Windows 窗体控件 [C++], 属性"
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：调用 Windows 窗体控件的属性和方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由于 [CWinFormsView::GetControl](../Topic/CWinFormsView::GetControl.md) 返回指向 <xref:System.Windows.Forms.Control?displayProperty=fullName> 的指针，而不是指向 `WindowsControlLibrary1::UserControl1` 的指针，因此最好添加一个用户控件类型的成员并在 [IView::OnInitialUpdate](../Topic/IView::OnInitialUpdate.md) 中将其初始化。  现在，可以使用 `m_ViewControl` 调用方法和属性。  
  
 本主题假定您以前已经学完[如何：创建用户控件并将它承载在对话框中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)和[如何：创建用户控件并承载 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
### 创建 MFC 宿主应用程序  
  
1.  打开在[如何：创建用户控件并承载 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)中创建的 MFC 应用程序。  
  
2.  将下行添加到 MFC02View.h 中 `CMFC02View` 类声明的 public overrides 节。  
  
     `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`  
  
3.  添加 OnInitialupdate 的重写。  
  
     显示**“属性”**窗口 \(F4\)。  在**“类视图”**\(Ctrl\+Shift\+C\) 中，选择 CMFC02View 类。  在**“属性”**窗口中，选择“重写”图标。  将列表向下滚动到 OnInitialUpdate。  单击下拉列表并选择\<Add\>。  确保 In MFC02View.cpp. 函数的正文如下所示：  
  
    ```  
    CWinFormsView::OnInitialUpdate();  
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());  
    m_ViewControl->textBox1->Text = gcnew System::String("hi");  
    ```  
  
4.  生成并运行该项目。  
  
     在**“生成”**菜单上，单击**“生成解决方案”**。  
  
     在**“调试”**菜单上，单击**“开始执行\(不调试\)”**。  
  
     请注意，文本框现在已初始化。  
  
## 请参阅  
 [以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)