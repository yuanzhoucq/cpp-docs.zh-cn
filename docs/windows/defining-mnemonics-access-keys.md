---
title: 如何：定义控制访问权限和值 (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.combo
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
ms.openlocfilehash: c49913597f51ef231073b89d60ad9718b1113f44
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041479"
---
# <a name="how-to-define-control-access-and-values-c"></a>如何：定义控制访问权限和值 (C++)

## <a name="tab-order"></a>Tab 键顺序

Tab 键顺序为依据的顺序**选项卡**键将输入的焦点从一个控件移到下一个对话框中。 通常从左到右、 从上到下一个对话框中，将继续 tab 键顺序。 每个控件都**Tabstop**属性，用于确定控件是否接收输入的焦点。

- 若要设置输入的焦点的控件，在[属性窗口](/visualstudio/ide/reference/properties-window)，选择**True**或**False**中**Tabstop**属性。

即便是那些没有**Tabstop**属性设置为**True**需要是 tab 键顺序，尤其是对于不包含标题的控件的一部分。 包含相关控件的访问键的静态文本注释后面必须紧跟相关的控件的 tab 键顺序。

> [!NOTE]
> 如果对话框包含重叠的控件，则更改 tab 键顺序可能会更改控件的显示的方式。 基于任何重叠的控件的 tab 键顺序将它们之前始终显示控件的更高版本中的 tab 键顺序。

- 若要查看当前的所有控件的 tab 键顺序，请转到菜单**格式** > **tab 键顺序**，或按**Ctrl** + **D**.

   每个控件的左上角的数字的当前选项卡顺序显示其位置。

- 若要更改的所有控件的 tab 键顺序，请转到菜单**格式** > **tab 键顺序**并选择所需的顺序中的每个控件设置 tab 键顺序**选项卡**密钥若要遵循。

- 若要更改两个或多个控件的 tab 键顺序，请转到菜单**格式** > **tab 键顺序**。 按住**Ctrl**密钥，然后选择的控件，其中按顺序的更改将开始，然后释放**Ctrl**密钥，然后选择所需的顺序中的控件**选项卡**密钥按照从该点。

   例如，如果你想要更改控件的顺序`7`通过`9`，按住**Ctrl**，然后选择的控件`6`第一个。

- 若要将特定控件设置为数字`1`，或者第一次 tab 键顺序中，双击该控件。

> [!TIP]
> 一旦您进入**tab 键顺序**模式中，按**Esc**或**Enter**退出**tab 键顺序**模式和禁用更改 tab 键顺序的能力。

## <a name="mnemonics-access-keys"></a>助记键 （访问键）

通常情况下，键盘用户输入的焦点从一个控件移动到另一个中使用的对话框**选项卡**并**箭头**密钥。 但是，可以定义允许用户通过按一个键选择一个控件的访问键 （助记键或容易记忆的名称）。

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>若要定义具有可见标题 （下压按钮、 复选框和单选按钮） 的控件的访问键

1. 选择对话框的上的控件。

1. 中[属性窗口](/visualstudio/ide/reference/properties-window)，在**标题**属性中，键入新名称进行控制，键入 & 符 (`&`) 要将该控件的访问密钥作为字母前。 例如 `&Radio1`。

1. 按 **Enter**。

   在显示的标题以指示访问密钥，例如，会出现下划线**R**adio1。

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>若要定义没有可见标题的控件的访问键

1. 通过使用使控件的标题**静态文本**控制[工具箱](/visualstudio/ide/reference/toolbox)。

1. 在静态文本标题中，输入与号 (`&`) 所需的访问密钥作为字母前。

1. 请确保静态文本控件紧跟其 tab 键顺序标记的控件。

> [!NOTE]
> 对话框中的所有访问键应都是唯一的。 若要检查重复的访问密钥，请转到菜单**格式** > **检查助记键**。

## <a name="combo-box-values"></a>组合框值

可以将值添加到组合框控件中，只要您具有**对话框编辑器**打开。

> [!TIP]
> 它是一个好办法将所有值都添加到组合框*之前*大小的框中**对话框编辑器**，或可能会截断应在组合框控件中显示的文本。

### <a name="to-enter-values-into-a-combo-box-control"></a>若要在组合框控件中输入值

1. 通过选择它来选择组合框控件。

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，向下滚动到**数据**属性。

   > [!NOTE]
   > 如果要显示按类型分组的属性**数据**将出现在**杂项**属性。

1. 选择的值域**数据**属性并键入你的数据值，用分号分隔。

   > [!NOTE]
   > 请勿放入值之间的空间，因为空格会按字母顺序排列在下拉列表中。

1. 按**Enter**完后添加值。

扩大的组合框下拉部分的信息，请参阅[设置组合框及其下拉列表的大小](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)。

> [!NOTE]
> 无法将值添加到 Win32 项目使用此过程 (**数据**属性将 Win32 项目灰显)。 因为 Win32 项目没有添加此功能的库，你必须以编程方式添加到 Win32 项目与组合框的值。

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>若要在组合框中测试的值的外观

1. 输入中的值后**数据**属性中，选择**测试**按钮[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

1. 请重试整个值列表中向下滚动。 显示的值中键入与完全**数据**属性中的**属性**窗口。 不不存在任何拼写或大小写检查。

1. 按**Esc**回到**对话框的**编辑器。

## <a name="radio-button-values"></a>单选按钮值

当向对话框添加单选按钮时，将它们视为一组通过设置**组**属性中的**属性**组中的第一个按钮的窗口。 然后该单选按钮的控件 ID 出现在 [添加成员变量向导](../ide/add-member-variable-wizard.md)中，让你可以添加单选按钮组的成员变量。

出现在对话框中，可以具有多个组单选按钮。 添加每个组，请使用以下过程。

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>向对话框添加一组单选按钮

1. 选择单选按钮控件中的[工具箱窗口](/visualstudio/ide/reference/toolbox)和放置控件的位置在对话框中选择的位置。

1. 重复上述步骤以添加所需的任意多个单选按钮。 请确保组中的单选按钮是连续的 tab 键顺序。

1. 在 [属性窗口](/visualstudio/ide/reference/properties-window)中，请将按照 Tab 键顺序排列的第一个单选按钮的 **组** 属性  设置为 **True**。

   更改**组**属性设置为**True**将 WS_GROUP 样式添加到资源脚本的对话框对象中的按钮条目并阻止用户可以在中的一次选择多个单选按钮按钮组 （如果用户选择一个单选按钮，组中其他都被清除）。

   > [!NOTE]
   > 只有组中第一个单选按钮的 **组** 属性应设置为 **True**。 如果不是按钮组的一部分的其他控件，设置**组**的第一个控件的属性 *，则将组外*到**True**也。 你可以快速确定使用的组之外的第一个控件**Ctrl**+**D**若要查看的 tab 键顺序。

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>添加单选按钮组的成员变量

1. 右键单击 tab 键顺序中的第一个单选按钮控件 (主导控件和一个**组**属性设置为**True**)，然后选择**添加变量**。

1. 在 [添加成员变量向导](../ide/add-member-variable-wizard.md)中，选择 **“控制变量”** 复选框，然后选择 **“值”** 单选按钮。

   - 在 **“变量名称”** 框中键入新成员变量的名称。

   - 在**变量类型**列表框中，选择**int**或类型*int*。

   现在可以通过修改代码来指定哪个单选按钮为选中状态。 例如，`m_radioBox1 = 0;`选择第一个单选按钮组中。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[管理对话框控件](controls-in-dialog-boxes.md)<br/>
[如何：添加、编辑或删除控件](adding-editing-or-deleting-controls.md)<br/>
[如何：布局控件](arrangement-of-controls-on-dialog-boxes.md)<br/>