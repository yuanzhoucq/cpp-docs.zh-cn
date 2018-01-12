---
title: "如何： 在对话框中创建用户控件并承载 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 81a618c46f08366b9de2a02cbf84f73d42e7b108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>如何：创建用户控件并将它承载在对话框中
这篇文章中的步骤假定你要创建基于对话框的 ([CDialog 类](../mfc/reference/cdialog-class.md)) Microsoft 基础类 (MFC) 项目，但你还可以添加对 Windows 窗体控件的支持到一个现有的 MFC 对话框。  
  
### <a name="to-create-the-net-user-control"></a>若要创建.NET 用户控件  
  
1.  创建一个名为的 Visual C# Windows 窗体控件库项目`WindowsFormsControlLibrary1`。  
  
     在 **文件** 菜单上，单击 **新建** ，然后单击 **项目**。 在**Visual C#**文件夹，选择**Windows 窗体控件库**。  
  
     接受`WindowsFormsControlLibrary1`通过单击项目名称**确定**。  
  
     默认情况下，.NET 控件的名称将为`UserControl1`。  
  
2.  添加到的子控件`UserControl1`。  
  
     在**工具箱**，打开**所有 Windows 窗体**列表。 拖动**按钮**控制转移到`UserControl1`设计图面。  
  
     此外添加**文本框中**控件。  
  
3.  在**解决方案资源管理器**，双击**UserControl1.Designer.cs**以将其打开以进行编辑。 更改文本框中和从按钮的声明`private`到`public`。  
  
4.  生成项目。  
  
     在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
### <a name="to-create-the-mfc-host-application"></a>若要创建 MFC 主机应用程序  
  
1.  创建 MFC 应用程序项目。  
  
     在 **文件** 菜单上，单击 **新建** ，然后单击 **项目**。 在**Visual c + +**文件夹，选择**MFC 应用程序**。  
  
     在“名称”框中键入 `MFC01`。 解决方案将设置更改为**将添加到解决方案**。 单击 **“确定”**。  
  
     在**MFC 应用程序向导**，对于应用程序类型，选择**基于对话框**。 接受其余的默认设置，然后单击**完成**。 这将创建的 MFC 应用程序在 MFC 对话框。  
  
2.  MFC 对话框中添加一个占位符控件。  
  
     上**视图**菜单上，单击**资源视图**。 在**资源视图**，展开**对话框**文件夹并双击`IDD_MFC01_DIALOG`。 对话框资源将显示**资源编辑器**。  
  
     在**工具箱**，打开**对话框编辑器**列表。 拖动**静态文本**控件添加到对话框资源。 **静态文本**控件将充当.NET Windows 窗体控件的占位符。 其大小调整至接近 Windows 窗体控件的大小。  
  
     在**属性**窗口中，更改**ID**的**静态文本**控制转移到`IDC_CTRL1`和更改**TabStop**属性**True**。  
  
3.  配置公共语言运行时 (CLR) 支持的项目。  
  
     在**解决方案资源管理器**，MFC01 项目节点，右键单击，然后单击**属性**。  
  
     在**属性页**对话框中，在**配置属性**，选择**常规**。 在**项目默认值**部分中，设置**公共语言运行时支持**到**公共语言运行时支持 (/ clr)**。  
  
     下**配置属性**，展开**C/c + +**和选择**常规**节点。 设置**调试信息格式**到**程序数据库 (/Zi)**。  
  
     选择**代码生成**节点。 设置**启用最小重新生成**到**否 (/ Gm-)**。 此外设置**基本运行时检查**到**默认**。  
  
     单击**确定**以应用更改。  
  
4.  添加对.NET 控件的引用。  
  
     在**解决方案资源管理器**，右键单击 MFC01 项目节点，然后单击**添加**，**引用**。 上**属性页**，单击**添加新引用**，选择**WindowsFormsControlLibrary1** (下**项目**选项卡)，然后单击**确定**。 这将添加引用的形式[/FU](../build/reference/fu-name-forced-hash-using-file.md)编译器选项，以使程序将进行编译。 它还会将一份 WindowsFormsControlLibrary1.dll \MFC01\ 项目文件夹中，以便将运行程序。  
  
5.  在 stdafx.h 文件中，找到以下行：  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     它的上方，添加以下行：  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  添加代码以创建托管的控件。  
  
     首先，声明托管的控件。 在 mfc01dlg.h 中，请转到对话框类的声明和受保护范围内，如下所示添加用户控件的数据成员。  
  
    ```  
    class CMFC01Dlg : public CDialog  
    {  
       // ...  
       // Data member for the .NET User Control:  
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;  
    ```  
  
     接下来，提供托管控件的实现。 在 MFC01Dlg.cpp，在对话框中重写的`CMFC01Dlg::DoDataExchange`生成 MFC 应用程序向导 (不`CAboutDlg::DoDataExchange`，即在同一文件中)，添加以下代码创建托管的控件并将其与静态占位符 IDC_CTRL1 关联。  
  
    ```  
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
    {  
       CDialog::DoDataExchange(pDX);  
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);  
    }  
    ```  
  
7.  生成并运行该项目。  
  
     在**解决方案资源管理器**，右键单击**MFC01** ，然后单击**设为启动项目**。  
  
     在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
     上**调试**菜单上，单击**启动而不调试**。 MFC 对话框中应显示 Windows 窗体控件。  
  
## <a name="see-also"></a>请参阅  
 [在 MFC 对话框中承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)