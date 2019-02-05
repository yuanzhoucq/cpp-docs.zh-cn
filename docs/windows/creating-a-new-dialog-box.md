---
title: 创建一个对话框 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: 928432000fb9a6347433b78b224e15f07ce810d2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742643"
---
# <a name="creating-a-dialog-box-c"></a>创建一个对话框 （c + +）

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-create-a-new-dialog-box"></a>若要创建新的对话框

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**添加资源**从快捷菜单。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 在中**添加资源**对话框中，选择**对话框**中**资源类型**列表，然后选择**新建**。

   如果一个加号 (**+**) 的旁边将出现**对话框**资源类型，这意味着对话框模板都可用。 选择加号以展开模板列表中的，选择一个模板，然后选择**新建**。

   在中打开新建对话框**对话框**编辑器。

   此外可以[在对话框编辑器中的现有对话框打开进行编辑](../windows/viewing-and-editing-resources-in-a-resource-editor.md)。

## <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>若要创建用户无法退出的对话框

可以创建用户无法退出的运行时对话框。 这种类型的对话框对于登录、应用程序或文档锁定非常有用。

1. 在对话框的“属性”  窗格中，将“系统菜单”  属性设置为“false” 。

   此设置将禁用对话框系统菜单并**关闭**按钮。

1. 在对话框窗体中，删除“取消”  和“确定”  按钮。

   在运行时，用户无法退出具有以下特征的模式对话框。

若要启用这种类型的对话框中的测试，测试对话框函数检测何时**Esc**按下。 (**Esc**是也称为 VK_ESCAPE 虚拟键。)无论方式对话框的设计为在运行时的行为，您可以通过按结束测试模式下**Esc**。

> [!NOTE]
> 对于 MFC 应用程序，创建一个对话框，用户无法退出，你必须重写的默认行为`OnOK`并`OnCancel`因为即使删除关联的按钮，则仍可对话框的取消按**输入**或**Esc**。

有关如何将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[如何：创建资源](../windows/how-to-create-a-resource.md)<br/>
[资源文件](../windows/resource-files-visual-studio.md)<br/>
[对话框编辑器](../windows/dialog-editor.md)