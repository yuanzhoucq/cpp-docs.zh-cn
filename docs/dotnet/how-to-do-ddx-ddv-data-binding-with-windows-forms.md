---
title: "如何：使用 Windows 窗体执行 DDX/DDV 数据绑定 | Microsoft Docs"
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
  - "MFC [C++], 承载 Windows 窗体控件"
  - "Windows 窗体 [C++], MFC 支持"
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 Windows 窗体执行 DDX/DDV 数据绑定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[DDX\_ManagedControl](../Topic/DDX_ManagedControl.md) 会调用 [CWinFormsControl::CreateManagedControl](../Topic/CWinFormsControl::CreateManagedControl.md) 来创建与资源控件 ID 匹配的控件。  如果（在向导生成的代码中）将 `DDX_ManagedControl` 用于 `CWinFormsControl` 控件，则不应该对同一控件显式调用 `CreateManagedControl`。  
  
 在 [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md) 中调用 `DDX_ManagedControl` 可以根据资源 ID 来创建控件。  对于数据交换，不需要对 Windows 窗体控件使用 DDX\/DDV 函数。  可以在对话框（或视图）类的 `DoDataExchange` 方法中插入代码以访问托管控件的属性，如下例所示。  
  
 下面的示例演示如何将本机 C\+\+ 字符串绑定到 .NET 用户控件。  
  
## 示例  
 下面的示例为 MFC 字符串 `m_str` 与 .NET 用户控件的用户定义的 `NameText` 属性进行 DDX\/DDV 数据绑定。  
  
 当 [CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md) 第一次调用 `CMyDlg::DoDataExchange` 时创建该控件，因此，引用 `m_UserControl` 的任何代码都必须在 `DDX_ManagedControl` 调用之后。  
  
 可以在从[如何：创建用户控件并将它承载在对话框中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)中创建的 MFC01 应用程序中实现此代码。  
  
 将以下代码放在 CMFC01Dlg 的声明中：  
  
```  
class CMFC01Dlg : public CDialog  
{  
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;  
   CString m_str;  
};  
```  
  
## 示例  
 将以下代码放在 CMFC01Dlg 的实现中：  
  
```  
void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
{  
   CDialog::DoDataExchange(pDX);  
   DDX_ManagedControl(pDX, IDC_CTRL1, m_MyControl);  
  
   if (pDX->m_bSaveAndValidate) {  
      m_str = m_MyControl->textBox1->Text;  
   } else  
   {  
      m_MyControl->textBox1->Text = gcnew System::String(m_str);  
   }  
}  
```  
  
## 示例  
 现在，我们将为“确定”按钮的单击添加处理程序方法。  单击**“资源视图”**选项卡。  在“资源视图”中，双击 `IDD_MFC01_DIALOG`。  对话框资源将显示在“资源编辑器”中。  然后双击“确定”按钮。  
  
 按如下方式定义处理程序。  
  
```  
void CMFC01Dlg::OnBnClickedOk()  
{  
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));  
   OnOK();  
}  
```  
  
## 示例  
 并将下行添加到 BOOL CMFC01Dlg::OnInitDialog\(\) 的实现中。  
  
```  
m_MyControl.GetControl()->textBox1->Text = "hello";  
```  
  
 现在可以生成并运行应用程序。  请注意，当应用程序关闭时，文本框中的任何文本将显示在弹出消息框中。  
  
## 请参阅  
 [CWinFormsControl Class](../mfc/reference/cwinformscontrol-class.md)   
 [DDX\_ManagedControl](../Topic/DDX_ManagedControl.md)   
 [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md)