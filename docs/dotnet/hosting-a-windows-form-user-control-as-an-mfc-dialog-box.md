---
title: "以 MFC 对话框的形式承载 Windows 窗体用户控件 | Microsoft Docs"
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
  - "承载 Windows 窗体控件 [C++]"
  - "MFC [C++], Windows 窗体支持"
  - "Windows 窗体 [C++], 作为 MFC 对话框承载"
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# 以 MFC 对话框的形式承载 Windows 窗体用户控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供模板类 [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md)，以便可以在模式或无模式 MFC 对话框中承载 Windows 窗体用户控件 \(<xref:System.Windows.Forms.UserControl>\)。  `CWinFormsDialog` 是从 MFC 类 [CDialog](../mfc/reference/cdialog-class.md) 派生的，所以该对话框可以以模式或无模式方式启动。  
  
 `CWinFormsDialog` 用以承载用户控件的过程与 [在 MFC 对话框中承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md) 中描述的类似。  但是，`CWinFormsDialog` 管理用户控件的初始化和承载，因此不必手动编程。  
  
 有关能够显示与 MFC 一起使用的 Windows 窗体的示例应用程序信息，请参阅 [MFC 与 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
### 创建 MFC 宿主应用程序  
  
1.  创建 MFC 应用程序项目。  
  
     在**“文件”**菜单上，选择**“新建”**，然后单击**“项目”**。  在**“Visual C\+\+”**文件夹中，选择**“MFC 应用程序”**。  
  
     在**“名称”**框中，输入 `MFC03`，并将“解决方案”设置更改为**“添入解决方案”**。单击**“确定”**。  
  
     在**“MFC 应用程序向导”**中，接受所有默认值，然后单击**“完成”**。  这就创建了一个具有多文档界面的 MFC 应用程序。  
  
2.  配置项目。  
  
     在“解决方案资源管理器”中，右击“MFC03”项目节点并选择“属性”。  将显示**“属性页”**对话框。  
  
     在**“属性页”**对话框中的**“配置属性”**树控件中，选择**“常规”**，然后在**“项目默认值”**部分中，将**“公共语言运行时支持”**设置为**“公共语言运行时支持 \(\/clr\)”**。  单击**“确定”**。  
  
3.  向 .NET 控件添加引用。  
  
     在“解决方案资源管理器”中，右击“MFC03”项目节点，然后选择“添加”、“引用”。  在“属性页”中，单击“添加新引用”，选择“WindowsControlLibrary1”（在“项目”选项卡下），然后单击“确定”。  此操作添加一个 [\/FU](../build/reference/fu-name-forced-hash-using-file.md) 编译器选项形式的引用，以便程序进行编译；它还将 WindowsControlLibrary1.dll 复制到 `MFC03` 项目目录中，以便程序运行。  
  
4.  将 `#include <afxwinforms.h>` 添加到 stdafx.h 中现有 `#include` 语句的末尾。  
  
5.  添加一个作为 `CDialog` 子类的新类。  
  
     右击项目名称并添加一个作为 `CDialog` 子类的 MFC 类（名为 CHostForWinForm）。  由于您不需要对话框资源，则可以删除其资源 ID（选择“资源视图”，展开“对话框”文件夹，删除 IDD\_HOSTFORWINFORM 资源。然后删除代码中对该 ID 的所有引用。）  
  
6.  将 CHostForWinForm.h 和 CHostForWinForm.cpp 文件中的 `CDialog` 替换为 `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`。  
  
7.  对 CHostForWinForm 类调用 DoModal。  
  
     在 MFC03.cpp 中，添加 `#include "HostForWinForm.h"`。  
  
     在 CMFC03App::InitInstance 定义中的 return 语句之前，添加：  
  
     `CHostForWinForm m_HostForWinForm;`  
  
     `m_HostForWinForm.DoModal();`  
  
8.  生成并运行该项目。  
  
     在**“生成”**菜单上，单击**“生成解决方案”**。  
  
     在**“调试”**菜单上，单击**“开始执行\(不调试\)”**。  
  
     接下来，将添加代码，用来从 MFC 应用程序监视 Windows 窗体上控件的状态。  
  
9. 添加 OnInitDialog 的处理程序。  
  
     显示**“属性”**窗口 \(F4\)。  在**“类视图”**中，选择“CHostForWinForm”。  在“属性”窗口中，选择 overrides，并在 OnInitDialog 所在的行中，单击左列并选择 \<添加\>。  这将向 CHostForWinForm.h 中添加下行：  
  
    ```  
    virtual BOOL OnInitDialog();  
    ```  
  
10. 按如下方式（在 CHostForWinForm.cpp 中）定义 OnInitDialog：  
  
    ```  
    BOOL CHostForWinForm::OnInitDialog() {  
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();  
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);  
       return TRUE;  
    }  
    ```  
  
11. 接下来，添加 OnButton1 处理程序。  将以下行添加到 CHostForWinForm.h 中 CHostForWinForm 类的 public 节中：  
  
    ```  
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );  
  
    BEGIN_DELEGATE_MAP( CHostForWinForm )  
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );  
    END_DELEGATE_MAP()  
    ```  
  
     在 CHostForWinForm.cpp 中，添加如下定义：  
  
    ```  
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )   
    {  
       System::Windows::Forms::MessageBox::Show("test");  
    }  
    ```  
  
12. 生成并运行该项目。  当您单击该按钮（位于 Windows 窗体上）时，将运行 MFC 应用程序中的代码。  
  
     接下来，将添加代码，用来从 MFC 代码中显示 Windows 窗体上文本框中的值。  
  
13. 在 CHostForWinForm.h 中 CHostForWinForm 类的 public 节中，添加如下声明：  
  
    ```  
    CString m_sEditBoxOnWinForm;  
    ```  
  
14. 在 CHostForWinForm.cpp 中的 DoDataExchange 定义中，向该函数的末尾添加以下三行：  
  
    ```  
    if (pDX->m_bSaveAndValidate)  
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);  
    else  
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);  
    ```  
  
15. 在 CHostForWinForm.cpp 中的 OnButton1 定义中，向该函数的末尾添加以下三行：  
  
    ```  
    this->UpdateData(TRUE);  
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);  
    System::Windows::Forms::MessageBox::Show(z);  
    ```  
  
16. 生成并运行该项目。  
  
## 请参阅  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>   
 [在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)