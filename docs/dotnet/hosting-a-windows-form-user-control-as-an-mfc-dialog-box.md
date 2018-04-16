---
title: "承载 Windows 窗体用户控件作为 MFC 对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7ad1d800619eb84a470dbc5e472e9191d13e8796
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>以 MFC 对话框的形式承载 Windows 窗体用户控件
MFC 提供一种模板类[CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) ，以便可以承载 Windows 窗体用户控件 (<xref:System.Windows.Forms.UserControl>) 在模式或无模式的 MFC 对话框中。 `CWinFormsDialog`派生自 MFC 类[CDialog](../mfc/reference/cdialog-class.md)，因此可以作为模式或无模式启动对话框。  
  
 该过程，`CWinFormsDialog`用来承载该用户控件是类似于中所述[承载 Windows 窗体用户控件在 MFC 对话框中](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)。 但是，`CWinFormsDialog`管理初始化和承载的用户控件，以便它不需要手动进行编程。  
  
 显示与 MFC 一起使用的 Windows 窗体的示例应用，请参阅[MFC 和 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
### <a name="to-create-the-mfc-host-application"></a>若要创建 MFC 主机应用程序  
  
1.  创建 MFC 应用程序项目。  
  
     上**文件**菜单上，选择**新建**，然后单击**项目**。 在**Visual c + +**文件夹，选择**MFC 应用程序**。  
  
     在**名称**框中，输入`MFC03`和解决方案将设置更改为**将添加到解决方案**。单击**确定**。  
  
     在**MFC 应用程序向导**，接受所有默认值，然后单击**完成**。 这将创建多文档界面 MFC 应用程序。  
  
2.  配置项目。  
  
     在**解决方案资源管理器**，右键单击**MFC03**项目节点，然后选择**属性**。 **属性页**对话框随即出现。  
  
     在**属性页**对话框中，在**配置属性**树控件中，选择**常规**，然后在**项目默认值**部分中，设置**公共语言运行时支持**到**公共语言运行时支持 (/ clr)**。 单击 **“确定”**。  
  
3.  添加对.NET 控件的引用。  
  
     在**解决方案资源管理器**，右键单击**MFC03**项目节点，选择**添加**，**引用**。 在**属性页**，单击**添加新引用**，选择 WindowsControlLibrary1 (下**项目**选项卡)，然后单击**确定**。 这将添加引用的形式[/FU](../build/reference/fu-name-forced-hash-using-file.md)编译器选项，以使程序将编译; 它还会将复制到 WindowsControlLibrary1.dll`MFC03`项目目录，以便运行程序。  
  
4.  添加`#include <afxwinforms.h>`到 stdafx.h 文件中，在末尾现有`#include`语句。  
  
5.  将新类添加该子类`CDialog`。  
  
     右键单击项目名称并添加该子类的 MFC 类 (调用 CHostForWinForm) `CDialog`。 由于不需要对话框资源，你可以删除的资源 ID （选择资源视图，展开对话框文件夹并删除 IDD_HOSTFORWINFORM 资源。  然后，删除任何引用的 id 在代码中。）。  
  
6.  替换`CDialog`中 CHostForWinForm.h 和 CHostForWinForm.cpp 文件与`CWinFormsDialog<WindowsControlLibrary1::UserControl1>`。  
  
7.  CHostForWinForm 类上调用 DoModal。  
  
     在 MFC03.cpp，添加`#include "HostForWinForm.h"`。  
  
     之前 CMFC03App::InitInstance 的定义中的返回语句，添加：  
  
     `CHostForWinForm m_HostForWinForm;`  
  
     `m_HostForWinForm.DoModal();`  
  
8.  生成并运行该项目。  
  
     在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
     上**调试**菜单上，单击**启动而不调试**。  
  
     接下来你将添加代码以监视从 MFC 应用程序的 Windows 窗体上控件的状态。  
  
9. 添加的处理程序 OnInitDialog。  
  
     显示**属性**窗口 (F4)。 在**类视图**，选择 CHostForWinForm。 在**属性**窗口中，选择重写和在 OnInitDialog 行中，单击左侧列中，然后选择\<添加 >。 这会向 CHostForWinForm.h 添加以下行：  
  
    ```  
    virtual BOOL OnInitDialog();  
    ```  
  
10. 定义 OnInitDialog （在 CHostForWinForm.cpp)，如下所示：  
  
    ```  
    BOOL CHostForWinForm::OnInitDialog() {  
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();  
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);  
       return TRUE;  
    }  
    ```  
  
11. 接下来添加 OnButton1 处理程序。 将以下行添加到中 CHostForWinForm.h 的 CHostForWinForm 类的公共部分：  
  
    ```  
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );  
  
    BEGIN_DELEGATE_MAP( CHostForWinForm )  
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );  
    END_DELEGATE_MAP()  
    ```  
  
     在 CHostForWinForm.cpp，添加此定义：  
  
    ```  
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )   
    {  
       System::Windows::Forms::MessageBox::Show("test");  
    }  
    ```  
  
12. 生成并运行该项目。 当你单击按钮，这将在 Windows 窗体上，将运行 MFC 应用程序中的代码。  
  
     接下来你将添加代码以显示从 MFC 代码中的值在 Windows 窗体的文本框。  
  
13. 在中 CHostForWinForm.h 的 CHostForWinForm 类的公共部分，添加以下声明：  
  
    ```  
    CString m_sEditBoxOnWinForm;  
    ```  
  
14. 在中 CHostForWinForm.cpp DoDataExchange 定义中，函数的末尾添加以下三个行：  
  
    ```  
    if (pDX->m_bSaveAndValidate)  
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);  
    else  
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);  
    ```  
  
15. 在中 CHostForWinForm.cpp OnButton1 定义中，函数的末尾添加以下三个行：  
  
    ```  
    this->UpdateData(TRUE);  
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);  
    System::Windows::Forms::MessageBox::Show(z);  
    ```  
  
16. 生成并运行该项目。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>   
 [在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)