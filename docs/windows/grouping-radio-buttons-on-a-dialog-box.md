---
title: 在对话框 （c + +） 上的单选按钮分组
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.grouping
helpviewer_keywords:
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls [C++], grouping radio buttons
- grouping controls
- radio buttons [C++], grouping on dialog boxes
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
ms.openlocfilehash: 1776823a7385499e5a01a04134fe31f42700e14b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665941"
---
# <a name="grouping-radio-buttons-on-a-dialog-box-c"></a>在对话框 （c + +） 上的单选按钮分组

当向对话框添加单选按钮时，将它们视为一组通过设置**组**属性中的**属性**组中的第一个按钮的窗口。 然后该单选按钮的控件 ID 出现在 [添加成员变量向导](../ide/add-member-variable-wizard.md)中，让你可以添加单选按钮组的成员变量。

一个对话框中可以有多组单选按钮，每个组都应使用以下过程添加。

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>向对话框添加一组单选按钮

1. 在[“工具箱窗口”](/visualstudio/ide/reference/toolbox) 中选择单选按钮控件，然后单击要将控件放置到对话框中的位置。

2. 重复执行第一步以根据需要添加多个单选按钮。 请确保组中的单选按钮是按照 Tab 键顺序连续排列的（有关详细信息，请参阅 [更改控件的 Tab 键顺序](../windows/changing-the-tab-order-of-controls.md)）。

3. 在 [属性窗口](/visualstudio/ide/reference/properties-window)中，请将按照 Tab 键顺序排列的第一个单选按钮的 **组** 属性  设置为 **True**。

   将 **组** 属性更改为 **True** 可将 WS_GROUP 样式添加到资源脚本的对话框对象的按钮条目中，并确保用户一次只能选择按钮组中的一个单选按钮（当用户单击一个单选按钮时，组中其他按钮都被清除）。

   > [!NOTE]
   > 只有组中第一个单选按钮的 **组** 属性应设置为 **True**。 如果你的不是按钮组的一部分的其他控件，设置**组**的第一个控件的属性 *，则将组外*到**True**以及。 您可以快速确定组外的第一个控件，通过按**Ctrl**+**D**若要查看的 tab 键顺序。

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>添加单选按钮组的成员变量

1. 按 Tab 键顺序右键单击第一个单选按钮控件（主导控件和 **组** 属性设置为 True 的控件）。

2. 从快捷菜单中选择 **“添加变量”**  。

3. 在 [添加成员变量向导](../ide/add-member-variable-wizard.md)中，选择 **“控制变量”** 复选框，然后选择 **“值”** 单选按钮。

4. 在 **“变量名称”** 框中键入新成员变量的名称。

5. 在中**变量类型**列表框中，选择**int**或类型`int`。

6. 现在可以通过修改代码来指定哪个单选按钮为选中状态。 例如，`m_radioBox1 = 0;`选择第一个单选按钮组中。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框上的控件排列](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)