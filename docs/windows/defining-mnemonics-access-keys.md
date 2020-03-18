---
title: 如何：定义控件访问和值（C++）
ms.date: 02/15/2019
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
ms.openlocfilehash: 8ebd8d48b68581bf00215b4ca14f5ac0a543a3c0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443900"
---
# <a name="how-to-define-control-access-and-values-c"></a>如何：定义控件访问和值（C++）

## <a name="tab-order"></a>Tab 键顺序

Tab 键顺序是**tab**键在对话框中将输入焦点从一个控件移动到下一个控件的顺序。 通常，tab 键顺序在对话框中从左到右，从上到下。 每个控件都有一个**Tabstop**属性，该属性确定控件是否接收输入焦点。

- 若要为控件设置输入焦点，请在 "[属性" 窗口](/visualstudio/ide/reference/properties-window)中，在 " **Tabstop** " 属性中选择 " **True** " 或 " **False** "。

即使控件未设置为**True** ，也需要是 tab 键**顺序的一部分**，特别是对于没有标题的控件。 对于包含相关控件的访问键的静态文本，在 tab 键顺序中必须紧跟在相关控件之前。

> [!NOTE]
> 如果您的对话框包含重叠控件，则更改 tab 键顺序可能会改变控件的显示方式。 位于 tab 键顺序后面的控件始终显示在选项卡顺序中位于它们前面的任何重叠控件的顶部。

- 若要查看所有控件的当前 tab 键顺序，请参阅菜单**格式** > **tab 键顺序**，或按**Ctrl** + **D**。

   每个控件左上角的一个数字按当前 tab 键顺序显示其位置。

- 若要更改所有控件的 tab 键顺序，请转到 "菜单**格式**" > **tab 键顺序**，并按**tab**键的顺序选择每个控件，设置 tab 键顺序。

- 若要更改两个或更多控件的 tab 键顺序，请转到 "菜单**格式**" > **tab 键顺序**。 按住**ctrl**键并选择要在其中开始进行更改的控件，然后释放**Ctrl**键并按您希望**Tab**键在该点后面遵循的顺序选择控件。

   例如，如果想要通过 `9`更改控件 `7` 的顺序，请按住**Ctrl**，然后选择 "控件 `6`"。

- 若要将特定控件设置为数字 `1`，或在 tab 键顺序中先单击，请双击该控件。

> [!TIP]
> 输入**Tab 键顺序**模式后，按**Esc**或**enter**退出**tab 键顺序**模式并禁用更改 tab 键顺序的功能。

## <a name="mnemonics-access-keys"></a>助记键（访问键）

通常，键盘用户在对话框中使用**Tab**键和**箭头**键将输入焦点从一个控件移动到另一个控件。 不过，您可以定义一个允许用户通过按单个键来选择控件的访问键（助记键或易于记住的名称）。

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>为具有可见标题（按钮、复选框和单选按钮）的控件定义访问键

1. 选择对话框上的控件。

1. 在 "[属性" 窗口](/visualstudio/ide/reference/properties-window)的 "**标题**" 属性中，为该控件键入一个新名称，并在所需的字母前键入与该控件的访问键相同的 "&" 符（`&`）。 例如 `&Radio1`。

1. 按 Enter。

   显示的标题中会出现一个下划线，指示访问密钥，例如**R**adio1。

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>为没有可见标题的控件定义访问键

1. 使用[工具箱](/visualstudio/ide/reference/toolbox)中的**静态文本**控件创建控件的标题。

1. 在静态文本标题中，在所需的字母前面键入与号（`&`）。

1. 确保静态文本控件紧靠在控件标记的控件的 tab 键顺序之前。

> [!NOTE]
> 对话框中的所有访问键都应该是唯一的。 若要检查重复的访问密钥，请访问菜单**格式** > **选中助记**键。

## <a name="combo-box-values"></a>组合框值

只要打开**对话框编辑器**，就可以向组合框控件添加值。

> [!TIP]
> 最好将所有值添加到组合框，*然后*在**对话框编辑器**中调整框的大小，也可以截断应显示在组合框中的文本。

### <a name="to-enter-values-into-a-combo-box-control"></a>向组合框控件输入值

1. 选择组合框控件。

1. 在 "[属性" 窗口](/visualstudio/ide/reference/properties-window)中，向下滚动到 "**数据**" 属性。

   > [!NOTE]
   > 如果要显示按类型分组的属性，**数据**将显示在 "**杂项**" 属性中。

1. 选择**数据**属性的 "值" 区域，然后键入数据值（用分号分隔）。

   > [!NOTE]
   > 不要在值之间加空格，因为空格会干扰下拉列表中的 alphabetizing。

1. 完成添加值后，按**enter** 。

有关放大组合框的下拉部分的信息，请参阅[设置组合框的大小及其下拉列表](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)。

> [!NOTE]
> 使用此过程时，不能向 Win32 项目添加值（Win32 项目的**数据**属性为灰显）。 由于 Win32 项目没有添加此功能的库，因此必须以编程方式将值添加到具有 Win32 项目的组合框。

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>测试组合框中值的外观

1. 在**Data**属性中输入值后，选择 "[对话框编辑器" 工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)上的 "**测试**" 按钮。

1. 尝试向下滚动整个值列表。 值与在 "**属性**" 窗口中的**数据**属性中键入的值完全一致。 没有拼写检查或大小写检查。

1. 按**Esc**返回**对话框**编辑器。

## <a name="radio-button-values"></a>单选按钮值

向对话框添加单选按钮时，可以通过在 "**属性**" 窗口中为组中的第一个按钮设置**组**属性将它们视为组。 然后该单选按钮的控件 ID 出现在 [添加成员变量向导](../ide/add-member-variable-wizard.md)中，让你可以添加单选按钮组的成员变量。

一个对话框中可以有多组单选按钮。 使用以下过程添加每个组。

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>向对话框添加一组单选按钮

1. 在 "[工具箱" 窗口](/visualstudio/ide/reference/toolbox)中选择单选按钮控件，然后在对话框中选择放置控件的位置。

1. 重复上述步骤，根据需要添加任意多个单选按钮。 请确保组中的单选按钮按 tab 键顺序连续排列。

1. 在 [属性窗口](/visualstudio/ide/reference/properties-window)中，请将按照 Tab 键顺序排列的第一个单选按钮的 **组** 属性 设置为 **True**。

   将**组**属性更改为**True**可将 WS_GROUP 样式添加到资源脚本的对话框对象的按钮条目中，并防止用户在按钮组中一次选择多个单选按钮（如果用户选择了一个单选按钮，则会清除组中的其他单选按钮）。

   > [!NOTE]
   > 只有组中第一个单选按钮的 **组** 属性应设置为 **True**。 如果其他控件不是按钮组的一部分，请将*组外*第一个控件的**组**属性设置为**True** 。 您可以通过使用**Ctrl**+**D**来查看 tab 键顺序，快速确定组外的第一个控件。

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>添加单选按钮组的成员变量

1. 右键单击 tab 键顺序中的第一个单选按钮控件（主导控件和**组**属性设置为**True**的控件），然后选择 "**添加变量**"。

1. 在 [添加成员变量向导](../ide/add-member-variable-wizard.md)中，选择“控制变量” 复选框，然后选择“值” 单选按钮。

   - 在“变量名称” 框中键入新成员变量的名称。

   - 在“变量类型” 列表框中，选择“int” 或键入“int”。

   现在可以通过修改代码来指定哪个单选按钮为选中状态。 例如，`m_radioBox1 = 0;` 选择组中的第一个单选按钮。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[管理对话框控件](controls-in-dialog-boxes.md)<br/>
[如何：添加、编辑或删除控件](adding-editing-or-deleting-controls.md)<br/>
[如何：布局控件](arrangement-of-controls-on-dialog-boxes.md)<br/>