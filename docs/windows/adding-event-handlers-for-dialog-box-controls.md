---
title: 添加事件处理程序对话框控件 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog Editor [C++], adding event handlers to controls
- controls [C++], event handlers
- dialog box controls [C++], events
- event handlers, for dialog box controls
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 156908a1611f8a1c8b22df61e6b789468753d25d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443080"
---
# <a name="adding-event-handlers-for-dialog-box-controls-c"></a>添加事件处理程序对话框控件 （c + +）

对于已与类关联的项目对话框，在创建事件处理程序时可以利用一些快捷方式。 您可以快速创建的默认控件通知事件或任何适用的 Windows 消息的处理程序。

### <a name="to-create-a-handler-for-the-default-control-notification-event"></a>若要创建的默认控件通知事件处理程序

1. 双击该控件。 **文本**编辑器随即打开。

2. 添加控件通知处理程序代码中的**文本**编辑器。

### <a name="to-create-a-handler-for-any-applicable-windows-message"></a>若要创建的任何适用的 Windows 消息的处理程序

1. 单击你想要处理的通知事件的控件。

2. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，单击**控件事件**按钮以显示与该控件关联的常见 Windows 事件的列表。 例如，标准**确定**按钮**有关**对话框会列出以下通知事件：

   - BN_CLICKED

   - BN_DOUBLECLICKED

   - BN_KILLFOCUS

   - BN_SETFOCUS

   > [!NOTE]
   > 或者，选择对话框的，然后单击**控件事件**按钮以在对话框中显示的所有控件的常见 Windows 事件列表。

3. 在中**属性**窗口中，单击事件处理旁的右侧列，然后选择建议的通知事件名称 (例如，`OnBnClickedOK`处理 BN_CLICKED)。

   > [!NOTE]
   > 或者，可以提供您的选择，而不是选择默认事件处理程序名称的事件处理程序名称。

   一旦选择了该事件，Visual Studio 将打开**文本编辑器**和显示事件处理程序的代码。 例如，以下代码添加默认`OnBnClickedOK`:

    ```cpp
    void CAboutDlg::OnBnClickedOk(void)
    {
        // TODO: Add your control notification handler code here
    }
    ```

如果你想要添加的事件处理程序类而不实现对话框中的一个，请使用[事件处理程序向导](../ide/event-handler-wizard.md)。 有关详细信息，请参阅[添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[默认控件事件](../windows/default-control-events.md)<br/>
[定义对话框控件的成员变量](../windows/defining-member-variables-for-dialog-controls.md)<br/>
[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)<br/>
[添加类](../ide/adding-a-class-visual-cpp.md)<br/>
[添加成员函数](../ide/adding-a-member-function-visual-cpp.md)<br/>
[添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[重写虚函数](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)  