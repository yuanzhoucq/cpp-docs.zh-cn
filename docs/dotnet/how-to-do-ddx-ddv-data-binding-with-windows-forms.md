---
title: 如何：执行 DDX-DDV 数据绑定与 Windows 窗体
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 558c763fd18cd1569ff23435bf6156b3117f117d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387313"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>如何：执行 DDX/DDV 数据绑定与 Windows 窗体

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)调用[CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol)创建控件匹配资源控件 id。 如果您使用`DDX_ManagedControl`有关`CWinFormsControl`控件 （在向导生成的代码），不应调用`CreateManagedControl`显式为相同的控件。

调用`DDX_ManagedControl`中[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)资源 Id 从创建控件。 数据交换，不需要将 DDX/DDV 函数与 Windows 窗体控件。 相反，可以将代码访问中的托管控件的属性放`DoDataExchange`对话框 （或视图） 类，如以下示例所示的方法。

下面的示例演示如何将绑定一个本机C++.NET 用户控件的字符串。

## <a name="example"></a>示例

下面是 MFC 字符串的 DDX/DDV 数据绑定的示例`m_str`与用户定义`NameText`.NET 用户控件的属性。

当创建该控件[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)调用`CMyDlg::DoDataExchange`第一次，因此任何代码，它引用`m_UserControl`后面必须出现`DDX_ManagedControl`调用。

可以在中创建的 MFC01 应用程序中实现此代码[如何：在对话框中创建用户控件并承载](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。

CMFC01Dlg 声明中添加以下代码：

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>示例

CMFC01Dlg 的实现中添加以下代码：

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

现在我们将确定按钮添加单击处理程序方法。 单击**资源视图**选项卡。在资源视图中，双击`IDD_MFC01_DIALOG`。 对话框资源将显示在资源编辑器中。 然后双击确定按钮...

按如下所示定义处理程序。

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

你现在可以生成并运行应用程序。 请注意，将显示在弹出消息框中的任何文本在文本框中的应用程序关闭时。

## <a name="see-also"></a>请参阅

[CWinFormsControl 类](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
