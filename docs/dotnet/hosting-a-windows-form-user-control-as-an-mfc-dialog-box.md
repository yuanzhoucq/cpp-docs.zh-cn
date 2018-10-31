---
title: 承载 Windows 窗体用户控件作为 MFC 对话框 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 86a820e54e63c21c3ec4b9ace538bd6bfb4e9c0a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052851"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>以 MFC 对话框的形式承载 Windows 窗体用户控件

MFC 提供模板类[CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) ，以便可以承载 Windows 窗体用户控件 (<xref:System.Windows.Forms.UserControl>) 模式或无模式 MFC 对话框中。 `CWinFormsDialog` 派生自 MFC 类[CDialog](../mfc/reference/cdialog-class.md)，因此可以作为模式或无模式启动的对话框。

该过程的`CWinFormsDialog`用以承载用户控件是类似于中所述[承载 Windows 窗体用户控件在 MFC 对话框](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)。 但是，`CWinFormsDialog`管理初始化和承载用户控件，以便它不必手动编程。

显示与 MFC 一起使用的 Windows 窗体的示例应用程序，请参阅[MFC 和 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。

### <a name="to-create-the-mfc-host-application"></a>若要创建 MFC 宿主应用程序

1. 创建 MFC 应用程序项目。

   上**文件**菜单中，选择**新建**，然后单击**项目**。 在中**Visual c + +** 文件夹，选择**MFC 应用程序**。

   在中**名称**框中，输入`MFC03`并将解决方案设置更改为**将添加到解决方案**。单击**确定**。

   在中**MFC 应用程序向导**，接受所有默认值，然后单击**完成**。 这将创建具有多文档界面的 MFC 应用程序。

1. 配置项目。

   在中**解决方案资源管理器**，右键单击**MFC03**项目节点，然后选择**属性**。 **属性页**对话框随即出现。

   在中**属性页**对话框中**配置属性**树控件中，选择**常规**，然后在**项目默认值**部分中，设置**公共语言运行时支持**到**公共语言运行时支持 (/ clr)**。 单击 **“确定”**。

1. 添加对.NET 控件的引用。

   在中**解决方案资源管理器**，右键单击**MFC03**项目节点，然后选择**添加**，**引用**。 在中**属性页**，单击**添加新引用**，选择 WindowsControlLibrary1 (下**项目**选项卡)，然后单击**确定**。 这在的窗体添加的引用[/FU](../build/reference/fu-name-forced-hash-using-file.md)编译器选项，以便程序进行编译; 它还将 windowscontrollibrary1.dll 复制到`MFC03`项目目录，以便运行该程序。

1. 添加`#include <afxwinforms.h>`到末尾的现有 stdafx.h`#include`语句。

1. 添加一个新类的子类`CDialog`。

   右键单击项目名称，然后添加该子类的 MFC 类 (名为 CHostForWinForm) `CDialog`。 由于不需要对话框资源，可以删除的资源 ID (选择**资源视图**，展开**对话框**文件夹，然后删除`IDD_HOSTFORWINFORM`资源。  然后，删除所有引用的 id 在代码中。）。

1. 替换`CDialog`CHostForWinForm.h 和 CHostForWinForm.cpp 文件中`CWinFormsDialog<WindowsControlLibrary1::UserControl1>`。

1. 对 CHostForWinForm 类调用 DoModal。

   在 mfc03.cpp 中，添加`#include "HostForWinForm.h"`。

   在 cmfc03app::initinstance 定义中的 return 语句之前, 添加：

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. 生成并运行该项目。

   在 **“生成”** 菜单上，单击 **“生成解决方案”**。

   上**调试**菜单上，单击**启动但不调试**。

   接下来将添加代码以监视在 MFC 应用程序从 Windows 窗体上控件的状态。

9. 添加 OnInitDialog 的处理程序。

   显示**属性**窗口 (F4)。 在中**类视图**，选择 CHostForWinForm。 在中**属性**窗口中，选择重写并在 oninitdialog 所在的行，单击左侧列中，选择\<添加 >。 这将向 chostforwinform.h 中添加以下行：

    ```cpp
    virtual BOOL OnInitDialog();
    ```

10. 按如下所示定义 OnInitDialog （在 CHostForWinForm.cpp 中):

    ```
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

11. 接下来添加 OnButton1 处理程序。 将以下行添加到 CHostForWinForm.h 中 CHostForWinForm 类的 public 节：

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

12. 生成并运行该项目。 当单击按钮，这是 Windows 窗体上，将运行 MFC 应用程序中的代码。

   接下来将添加代码以显示从 MFC 代码中的值在 Windows 窗体的文本框。

13. 在 CHostForWinForm.h 中 CHostForWinForm 类的 public 节中，添加以下声明：

    ```
    CString m_sEditBoxOnWinForm;
    ```

14. 在 CHostForWinForm.cpp 中的 DoDataExchange 定义中，将添加到该函数的末尾的以下三行：

    ```
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

15. 在 CHostForWinForm.cpp 中的 OnButton1 定义中，将添加到该函数的末尾的以下三行：

    ```
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

16. 生成并运行该项目。

## <a name="see-also"></a>请参阅

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)