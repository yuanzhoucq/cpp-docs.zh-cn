---
title: 定义控制访问权限和值
ms.date: 11/04/2016
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
ms.openlocfilehash: 3a885ad57ba05304d51cb45d0b498d81ad37a148
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264850"
---
# <a name="defining-control-access-and-values"></a>定义控制访问权限和值

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="change-the-tab-order-of-controls"></a>更改控件的 tab 键顺序

Tab 键顺序为依据的顺序**选项卡**键将输入的焦点从一个控件移到下一个对话框中。 通常从左到右、 从上到下一个对话框中，将继续 tab 键顺序。 每个控件都**Tabstop**属性，用于确定控件是否接收输入的焦点。

### <a name="to-set-input-focus-for-a-control"></a>若要设置输入的焦点的控件

在中[属性窗口](/visualstudio/ide/reference/properties-window)，选择**True**或**False**中**Tabstop**属性。

即便是那些没有**Tabstop**属性设置为**True**需要是 tab 键顺序的一部分。 Tab 键顺序很重要，例如，当您[定义的访问键 （助记键）](../windows/defining-mnemonics-access-keys.md)没有标题的控件。 包含相关控件的访问键的静态文本注释后面必须紧跟相关的控件的 tab 键顺序。

> [!NOTE]
> 如果对话框包含重叠的控件，则更改 tab 键顺序可能会更改控件的显示的方式。 基于任何重叠的控件的 tab 键顺序将它们之前始终显示控件的更高版本中的 tab 键顺序。

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>若要在对话框中查看当前的所有控件的 tab 键顺序

上**格式**菜单中，选择**tab 键顺序**。

\- 或 -

- 按**Ctrl** + **D**。

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>若要更改的对话框中的所有控件的 tab 键顺序

1. 上**格式**菜单中，选择**tab 键顺序**。

   每个控件的左上角的数字的当前选项卡顺序显示其位置。

1. 通过单击所需的顺序在每个控件设置 tab 键顺序**选项卡**键遵循。

1. 按**Enter**退出**tab 键顺序**模式。

   > [!TIP]
   > 一旦您进入**tab 键顺序**模式下，可以按**Esc**或**Enter**可禁止更改 tab 键顺序。

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>若要更改两个或多个控件的 tab 键顺序

1. 从**格式**菜单中，选择**tab 键顺序**。

1. 指定将开始按顺序更改的位置。 第一次按下**Ctrl**键并选择控件，然后选择的要更改其顺序开始。

   例如，如果你想要更改控件的顺序`7`通过`9`，按住**Ctrl**，然后选择的控件`6`第一个。

   > [!NOTE]
   > 若要将特定控件设置为数字`1`（首先在 tab 键顺序），双击该控件。

1. 发行**Ctrl**键，然后选择所需的顺序中的控件**选项卡**键遵循从该点。

1. 按**Enter**退出**tab 键顺序**模式。

## <a name="define-mnemonics-access-keys"></a>定义助记键 （访问键）

通常情况下，键盘用户输入的焦点从一个控件移动到另一个中使用的对话框**选项卡**并**箭头**密钥。 但是，可以定义允许用户通过按一个键选择一个控件的访问键 （助记键或容易记忆的名称）。

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>若要定义具有可见标题 （下压按钮、 复选框和单选按钮） 的控件的访问键

1. 选择对话框的上的控件。

2. 中[属性窗口](/visualstudio/ide/reference/properties-window)，在**标题**属性中，键入新名称进行控制，键入 & 符 (`&`) 要将该控件的访问密钥作为字母前。 例如 `&Radio1`。

3. 按 **Enter**。

   在显示的标题以指示访问密钥，例如，会出现下划线**R**adio1。

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>若要定义没有可见标题的控件的访问键

1. 通过使用使控件的标题**静态文本**控制[工具箱](/visualstudio/ide/reference/toolbox)。

2. 在静态文本标题中，输入与号 (`&`) 所需的访问密钥作为字母前。

3. 请确保静态文本控件紧跟其 tab 键顺序标记的控件。

对话框中的所有访问键应都是唯一的。

### <a name="to-check-for-duplicate-access-keys"></a>若要检查重复的访问键

1. 上**格式**菜单上，单击**检查助记键**。

## <a name="add-values-to-a-combo-box-control"></a>将值添加到组合框控件

可以将值添加到组合框控件中，只要您具有**对话框**编辑器中，打开。

> [!TIP]
> 它是一个好办法将所有值都添加到组合框*之前*大小的框中**对话框**编辑器中，也可能会截断应在组合框控件中显示的文本。

### <a name="to-enter-values-into-a-combo-box-control"></a>若要在组合框控件中输入值

1. 通过单击选择组合框控件。

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，向下滚动到**数据**属性。

   > [!NOTE]
   > 如果要显示按类型分组的属性**数据**将出现在**杂项**属性。

1. 选择的值域**数据**属性并键入你的数据值，用分号分隔。

   > [!NOTE]
   > 不要将值之间的空间，因为空格会按字母顺序排列在下拉列表中。

1. 按**Enter**完后添加值。

扩大的组合框下拉部分的信息，请参阅[设置组合框及其下拉列表的大小](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)。

> [!NOTE]
> 无法将值添加到 Win32 项目使用此过程 (**数据**属性将 Win32 项目灰显)。 因为 Win32 项目没有添加此功能的库，你必须以编程方式添加到 Win32 项目与组合框的值。

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>若要在组合框中测试的值的外观

输入中的值后**数据**属性中，选择**测试**按钮[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

   请重试整个值列表中向下滚动。 显示的值中键入与完全**数据**属性中的**属性**窗口。 不不存在任何拼写或大小写检查。

   按**Esc**回到**对话框的**编辑器。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)