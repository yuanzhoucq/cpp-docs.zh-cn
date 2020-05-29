---
title: 如何：使用 Windows 窗体执行 DDX-DDV 数据绑定
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 31629a4db2559112ba49f5c069b08de7abdfc2db
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754358"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>如何：使用 Windows 窗体执行 DDX/DDV 数据绑定

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)调用[CWinForms 控制：：创建托管控制](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol)以创建与资源控制 ID 匹配的控件。 如果用于`DDX_ManagedControl`控件（在`CWinFormsControl`向导生成的代码中），则不应显式调用`CreateManagedControl`同一控件。

在`DDX_ManagedControl` [CWnd：:DoDataExchange 中](../mfc/reference/cwnd-class.md#dodataexchange)调用，从资源 ID 创建控件。 对于数据交换，您无需将 DDX/DDV 函数与 Windows 窗体控件一起使用。 相反，您可以将代码放在对话框（或视图）类`DoDataExchange`的方法中访问托管控件的属性，如以下示例所示。

下面的示例演示如何将本机C++字符串绑定到 .NET 用户控件。

## <a name="example"></a>示例

下面是 MFC 字符串的 DDX/DDV 数据绑定的示例，`m_str`该字符串具有 .NET 用户控件的用户定义`NameText`属性。

当[CDialog：：OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)首次调用`CMyDlg::DoDataExchange`时创建该控件，因此引用`m_UserControl`的任何代码都必须在`DDX_ManagedControl`调用后出现。

您可以在"[如何：在对话框中创建用户控制和主机"](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)中创建的 MFC01 应用程序中实现此代码。

在 CMFC01Dlg 的声明中放入以下代码：

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>示例

在 CMFC01Dlg 的实现中放入以下代码：

```cpp
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

现在，我们将添加处理程序方法，单击"确定"按钮。 单击"**资源视图"** 选项卡。在"资源视图"中，双`IDD_MFC01_DIALOG`击 。 对话框资源将显示在资源编辑器中。 然后双击"确定"按钮。

定义处理程序，如下所示。

```cpp
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>示例

并添加以下行的BOOL CMFC01Dlg实现：：onInitDialog（）。

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

现在可以构建并运行应用程序。 请注意，当应用程序关闭时，文本框中的任何文本都将显示在弹出消息框中。

## <a name="see-also"></a>请参阅

[CWinForms控制类](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd：:DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
