---
title: "如何： 调用属性和方法的 Windows 窗体控制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: eebbc955a0b44b686986e5bd1e753ec8809a3a1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>如何：调用 Windows 窗体控件的属性和方法
因为[CWinFormsView::GetControl](../mfc/reference/cwinformsview-class.md#getcontrol)返回一个指向<xref:System.Windows.Forms.Control?displayProperty=fullName>，并不是指向`WindowsControlLibrary1::UserControl1`，则最好添加用户控件类型的成员并将其在初始化[IView::OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate). 现在你可以调用方法和属性使用`m_ViewControl`。  
  
 本主题假定你以前已完成[如何： 在对话框中创建用户控件并承载](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)和[如何： 创建用户控件和主机 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
### <a name="to-create-the-mfc-host-application"></a>若要创建 MFC 主机应用程序  
  
1.  打开你在中创建的 MFC 应用程序[如何： 创建用户控件和主机 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
2.  将以下行添加到的公共重写部分`CMFC02View`类 MFC02View.h 中的声明。  
  
     `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`  
  
3.  有关 OnInitialupdate 添加一个替代。  
  
     显示**属性**窗口 (F4)。 在**类视图**(CTRL + SHIFT + C)，选择 CMFC02View 类。 在**属性**窗口中，为替代选择图标。 向下到 OnInitialUpdate 列表。 单击下拉列表，然后选择\<添加 >。 在 MFC02View.cpp。 请确保 OnInitialUpdate 函数体，如下所示：  
  
    ```  
    CWinFormsView::OnInitialUpdate();  
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());  
    m_ViewControl->textBox1->Text = gcnew System::String("hi");  
    ```  
  
4.  生成并运行该项目。  
  
     在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
     上**调试**菜单上，单击**启动而不调试**。  
  
     请注意，现在初始化文本框。  
  
## <a name="see-also"></a>请参阅  
 [以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)