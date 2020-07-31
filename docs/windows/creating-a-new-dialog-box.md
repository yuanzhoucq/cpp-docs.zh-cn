---
title: 如何：创建对话框（c + +）
ms.date: 02/15/2019
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
ms.openlocfilehash: 0d5e4836933f1ce32f28c7fd03c81be5b7d09fd9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222077"
---
# <a name="how-to-create-a-dialog-box-c"></a>如何：创建对话框（c + +）

"C + +" 对话框的位置和大小以及其中控件的位置和大小以对话单位来度量。 当你选择各个控件的值时，它们将显示在 Visual Studio 状态栏的右下角。

> [!NOTE]
> 如果你的项目尚未包含 .rc 文件，请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

## <a name="how-to"></a>如何

利用**对话框编辑器**，您可以：

### <a name="to-create-a-new-dialog-box"></a>创建新对话框

1. 在[资源视图](how-to-create-a-resource-script-file.md#create-resources)中，右键单击 *.rc*文件，然后选择 "**添加资源**"。

1. 在 "**添加资源**" 对话框中，选择 "**资源类型**" 列表中的 "**对话框**"，然后选择 "**新建**"。

   如果 **+** **对话框**资源类型旁边出现一个加号（），则表示对话框模板可用。 选择加号以展开模板列表，选择模板，然后选择 "**新建**"。

   新对话框将在**对话框编辑器**中打开。

您还可以在对话框编辑器中打开现有对话框进行编辑。

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>创建用户无法退出的对话框

你可以创建一个用户无法退出的运行时对话框。 这种类型的对话框对于登录、应用程序或文档锁定非常有用。

1. 在对话框的 "**属性**" 窗格中，将 "**系统菜单**" 属性设置为 **`false`** 。

   此设置将禁用对话框系统菜单和 "**关闭**" 按钮。

1. 在对话框窗体中，删除“取消” **** 和“确定” **** 按钮。

   在运行时，用户无法退出具有以下特征的模式对话框。

若要启用此类对话框的测试，测试对话框函数将在按下**Esc 键**时检测。 **Esc**也称为 VK_ESCAPE 虚拟键。 不管对话框在运行时的行为如何，您都可以通过按**Esc 键**来结束测试模式。

> [!NOTE]
> 对于 MFC 应用程序，若要创建用户无法退出的对话框，必须重写和的默认行为 `OnOK` ， `OnCancel` 因为即使删除关联按钮，仍可通过按**enter**或**Esc**来关闭该对话框。

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>指定对话框的位置和大小

您可以在 "[属性" 窗口](/visualstudio/ide/reference/properties-window)中设置属性，以指定在屏幕上显示对话框的位置。

- 布尔值**中心**属性。

   如果将值设置为**True**，则对话框将始终显示在屏幕的中心。 如果将此属性设置为**False**，则可以设置**XPos**和**YPos**属性。

- 用于显式定义对话框将出现在屏幕上的位置的**XPos**和**YPos**属性。

   这些位置属性是查看区域左上角的偏移量值，其定义为 `{X=0, Y=0}` 。

- 影响位置的**绝对对齐**属性。

   如果**为 True**，则坐标相对于屏幕。 如果**为 False**，则坐标相对于对话框所有者的窗口。

### <a name="to-test-a-dialog-box"></a>测试对话框

当您设计对话框时，无需编译程序即可模拟并测试其运行时行为。 在此模式中，您可以：

- 键入文本、从组合框列表中选择、打开或关闭选项，以及选择命令。

- 测试 Tab 键顺序。

- 测试控件的分组，如单选按钮和复选框。

- 在对话框中测试控件的键盘快捷键。

> [!NOTE]
> 模拟中不包含使用向导创建的对话框代码的连接。

当测试对话框时，它通常显示在与主程序窗口相对的位置。 如果已将 "对话框**绝对对齐**" 属性设置为 " **True**"，则该对话框将显示在相对于屏幕左上角的位置。

1. 当**对话框编辑器**为活动窗口时，请跳到 "菜单**格式**  >  **测试" 对话框**。

1. 若要结束模拟，请按**Esc** ，或选择正在测试的对话框中的 "**关闭**" 按钮。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[对话框编辑器](../windows/dialog-editor.md)<br/>
[如何：管理对话框控件](../windows/controls-in-dialog-boxes.md)<br/>
