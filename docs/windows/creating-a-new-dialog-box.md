---
title: 如何：创建一个对话框 （c + +）
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: c757c82978a5107374e6de2f8cff24319ed64f9c
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336470"
---
# <a name="how-to-create-a-dialog-box-c"></a>如何：创建一个对话框 （c + +）

位置和大小的 c + + 对话框中，和位置中，控件的大小以对话框单元为单位测量。 当选择 Visual Studio 状态栏的右下角显示各个控件和对话框中的值。

当您设计对话框中时，还可以模拟并测试其运行时行为，而无需编译您的程序。 在此模式中，您可以：

- 键入文本、从组合框列表中选择、打开或关闭选项，以及选择命令。

- 测试 Tab 键顺序。

- 测试控件的分组，如单选按钮和复选框。

- 在对话框中测试控件的键盘快捷键。

   > [!NOTE]
   > 与使用向导生成的对话框代码的连接不包括在此模拟中。

当测试对话框时，它通常显示在与主程序窗口相对的位置。 如果你已设置对话框的**Absolute Align**属性设置为**True**，对话框会显示在相对于屏幕的左上角的位置。

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

## <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>若要指定的位置和大小的对话框

有三个属性，您可以在设置[属性窗口](/visualstudio/ide/reference/properties-window)指定对话框将出现在屏幕上。 **Center**属性是一个布尔值; 如果将值设置为**True**，对话框中将始终显示在屏幕的中心。 如果设置为**False**，然后，可以设置**XPos**并**YPos**属性来显式定义在屏幕上将显示此对话框。 位置属性是从查看区域，该常数定义为左上角的偏移量的值`{X=0, Y=0}`。 位置也基于**Absolute Align**属性： 如果**True**，坐标是相对于屏幕; 如果**False**，坐标都相对于对话框所有者的窗口。

## <a name="to-test-a-dialog-box"></a>测试对话框

1. 当**对话框中**编辑器为活动窗口时，在菜单栏上的，选择**格式** > **测试对话框**。

1. 若要结束此模拟，按**Esc**或选择**关闭**要测试的对话框中的按钮。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[如何：创建资源](../windows/how-to-create-a-resource.md)<br/>
[资源文件](../windows/resource-files-visual-studio.md)<br/>
[对话框编辑器](../windows/dialog-editor.md)<br/>
[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>