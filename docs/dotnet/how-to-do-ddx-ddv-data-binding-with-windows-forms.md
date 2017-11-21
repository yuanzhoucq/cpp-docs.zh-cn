---
title: "如何： 执行 DDX DDV 数据绑定 Windows 窗体 |Microsoft 文档"
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
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d339be4d907e0cfaaea1e80830b3fe77b1cc09b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>如何：使用 Windows 窗体执行 DDX/DDV 数据绑定
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)调用[CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol)创建控件匹配资源控件 id。 如果你使用`DDX_ManagedControl`为`CWinFormsControl`控件 （在向导生成的代码），不应调用`CreateManagedControl`显式为同一个控件。  
  
 调用`DDX_ManagedControl`中[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)从资源 Id 创建控件。 对于数据交换，不需要使用 Windows 窗体控件与 DDX/DDV 函数。 相反，你可以将代码来访问托管控件中的属性放置`DoDataExchange`对话框 （或视图） 类，如以下示例所示的方法。  
  
 下面的示例演示如何将本机 c + + 字符串绑定到.NET 用户控件。  
  
## <a name="example"></a>示例  
 以下是 MFC 字符串的 DDX/DDV 数据绑定的示例`m_str`与用户定义`NameText`.NET 用户控件的属性。  
  
 当创建该控件[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)调用`CMyDlg::DoDataExchange`第一次，因此任何代码引用`m_UserControl`必须后`DDX_ManagedControl`调用。  
  
 你可以在中创建的 MFC01 应用程序中实现此代码[如何： 在对话框中创建用户控件并承载](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。  
  
 将下面的代码放在 CMFC01Dlg 的声明：  
  
```  
class CMFC01Dlg : public CDialog  
{  
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;  
   CString m_str;  
};  
```  
  
## <a name="example"></a>示例  
 将下面的代码放在 CMFC01Dlg 的实现：  
  
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
  
## <a name="example"></a>示例  
 现在我们将添加确定按钮的单击处理程序方法。 单击**资源视图**选项卡。在资源视图中，双击`IDD_MFC01_DIALOG`。 对话框资源将显示在资源编辑器中。 然后双击确定按钮...  
  
 按以下方式定义处理程序。  
  
```  
void CMFC01Dlg::OnBnClickedOk()  
{  
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));  
   OnOK();  
}  
```  
  
## <a name="example"></a>示例  
 并将以下行添加到 BOOL CMFC01Dlg::OnInitDialog() 的实现。  
  
```  
m_MyControl.GetControl()->textBox1->Text = "hello";  
```  
  
 你现在可以生成并运行应用程序。 请注意，在文本框中的任何文本将显示在弹出消息框中中，应用程序关闭时。  
  
## <a name="see-also"></a>另请参阅  
 [CWinFormsControl 类](../mfc/reference/cwinformscontrol-class.md)   
 [DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)   
 [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)