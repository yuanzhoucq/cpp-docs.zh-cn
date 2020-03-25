---
title: 快捷键编辑器（C++）
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator.F1
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [C++], accelerator key
- accelerator keys [C++]
- resource editors [C++], Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
- searching, in accelarator tables
- accelerator tables [C++], finding entries
- accelerator tables [C++], adding entries
- New Accelerator command
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
ms.openlocfilehash: 80ef6cc9ec956d0041c4aa3fb6a6211868cc9d73
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167558"
---
# <a name="accelerator-editor-c"></a>快捷键编辑器（C++）

快捷键对应表是一个C++ Windows 资源，其中包含快捷键列表（称为快捷键）和与它们关联的命令标识符。 一个程序可以拥有多个快捷键对应表。

通常情况下，快捷键用作程序命令的键盘快捷键，也可用于菜单或工具栏。 但是，快捷键对应表可用于为没有关联用户界面对象的命令定义组合键。

> [!TIP]
> 使用**快捷键编辑器**时，右键单击以显示常用命令的快捷菜单。 可用命令取决于指针所指向的内容。

可以使用 [类视图](/visualstudio/ide/viewing-the-structure-of-code) 将快捷键命令与代码挂接。 有关预定义快捷键的列表，请参阅[加速键](../windows/predefined-accelerator-keys.md)。

> [!NOTE]
> Windows 不允许创建空快捷键对应表。 如果创建的快捷键对应表中没有任何条目，在保存表时会被自动删除。

## <a name="accelerator-properties"></a>快捷键属性

你可以随时在[属性窗口](/visualstudio/ide/reference/properties-window)中设置快捷键属性。 你还可以使用**快捷键编辑器**来修改快捷键对应表中的快捷键属性。 使用 "**属性**" 窗口或 "**快捷键编辑器**" 所做的更改具有相同的结果，编辑会立即反映在快捷键对应表中。

**ID**属性引用程序代码中的每个快捷键对应表项。 此项是当用户按下快捷键或键组合时，程序接收的命令值。 若要使加速器与菜单项相同，请将**id**设置为相同的，只要快捷键对应表的**id**与菜单资源的**id**相同。

每个加速器**ID**都有三个属性：**修饰符**、**键**和**类型**

**修饰符**属性为快捷键设置控件键组合。

> [!NOTE]
> 在 "**属性**" 窗口中，**修饰符**属性显示为三个单独的**布尔**属性，所有这些属性都可以独立进行控制： **Alt**、 **Ctrl**和**Shift**。

下面是快捷键对应表中**修饰符**属性的合法条目：

   |值|说明|
   |-----------|-----------------|
   |无|用户仅按**键值**。<br/><br/>此值最有效地用于 ASCII/ANSI 值001到026，它被解释为 ^ A 到 ^ Z （**ctrl + a**到**ctrl + z**）。|
   |**Alt**|用户必须在**键值**前按**Alt** 。|
   |**Ctrl**|用户必须在**键值**之前按**Ctrl** ，这对于 ASCII 类型无效。|
   |**Shift**|用户必须在**键值**之前按**Shift**键。|
   |**Ctrl + Alt**|用户必须在**键值**之前按**Ctrl**和**Alt** ，而不能在 ASCII 类型上按 "无效"。|
   |**Ctrl + Shift**|用户必须在**键值**之前按**Ctrl**键，而不能在 ASCII 类型上按**Shift** 。|
   |**Alt + Shift**|用户必须在**键值**前按**Alt**和**Shift** ，这对于 ASCII 类型无效。|
   |**Ctrl + Alt + Shift**|用户必须在**键值**之前按**Ctrl**、 **Alt**和**Shift** ，而不能在 ASCII 类型上按 "无效"。|

**Key**属性设置要用作快捷键的实际密钥。

下面是快捷键对应表中的**键**属性的合法条目：

   |值|说明|
   |-----------|-----------------|
   |十进制格式的0到255之间的整数。|该值确定是否将值视为 ASCII 或 ANSI，如下所示：<br/><br/>   -一位数始终解释为相应的键，而不是 ASCII 或 ANSI 值。<br/>   -从1到26的值（在前面带有0时）被解释为 ^ A 到 ^ Z，这表示在按下 Ctrl 键的**同时**按下的字母的 ASCII 值。<br/>   -27-32 中的值始终解释为三位十进制值027到032。<br/>   -从033到255的值，无论前面是0还是 not，都将被解释为 ANSI 值。|
   |单个键盘字符。|大写字母 a-z 或数字 0-9 可以是 ASCII 值或虚拟键值。 任何其他字符均仅为 ASCII。|
   |在 a-z 范围内的单个键盘字符（仅大写），前面有一个插入符号（^），例如 ^ C。|此选项在按下**Ctrl**键的同时输入该键的 ASCII 值。|
   |任何有效的虚拟密钥标识符。|快捷键对应表中的下拉**键**框包含标准虚拟键标识符的列表。|

> [!NOTE]
> 输入 ASCII 值时，**修饰符**属性选项是有限的。 唯一可用的控制键是**Alt**键。

> [!TIP]
> 用于定义加速键的快捷方式是：右键单击快捷键对应表中的一个或多个条目，然后选择 "**下一键类型**"，然后在键盘上按任意键或键组合。
>
> "**编辑**" 菜单还提供了此**下一个按键类型**的命令。

**Type**属性确定与快捷键**ID**关联的快捷组合键是否被解释为 ASCII/ANSI 键值或虚拟键（VIRTKEY）组合。

- 如果**类型**属性是**ASCII**，则**修饰符**属性只能是 `None` 或 `Alt`，或者它可以有一个使用**Ctrl**键的快捷键，该快捷键通过使用 `^`前面的键来指定。

- 如果**Type**属性为**VIRTKEY**，则**修饰符**和**键值**的任意组合都有效。

> [!NOTE]
> 如果要在快捷键对应表中输入值并将值视为 ASCII/ANSI，请在表中选择条目的**类型**，然后从下拉列表中选择 " **ASCII** "。 但是，如果使用 "**编辑**" 菜单中的 "**下一键类型**" 命令来指定**密钥**，则在输入**密钥**代码*之前*，必须将**类型**属性从**VIRTKEY**更改为**ASCII** 。

## <a name="accelerator-tables"></a>快捷键对应表

在C++项目中，您可以使用**快捷键编辑器**中的就地编辑直接编辑快捷键对应表。

下面的过程引用标准属性页，但是，就地编辑和属性页方法具有相同的结果。 使用属性页或就地编辑所做的更改将立即反映在快捷键对应表中。

### <a name="to-edit-in-an-accelerator-table"></a>在快捷键对应表中编辑

1. 通过双击快捷键对应表中的图标来打开[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 选择表中的条目，并选择激活就地编辑。

1. 从下拉组合框中选择或键入就地进行更改：

   - 对于 " **ID**"，请从列表中选择或键入以进行编辑。

   - 对于 "**修饰符**"，请从列表中选择。

   - 对于 "**密钥**"，请从列表中选择或键入以进行编辑。

   - 对于 "**类型**"，请从列表中选择 " **ASCII** " 或 " **VIRTKEY** "。

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>在打开的快捷键对应表中查找项

1. 通过双击快捷键对应表中的图标来打开[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 选择列标题可按字母顺序对列的内容进行排序。 例如，选择 " **ID** " 可按字母顺序显示快捷键对应表中的所有 id。

   然后，可以浏览列表并找到该项。

### <a name="to-add-an-entry-to-an-accelerator-table"></a>向快捷键对应表添加项

1. 通过双击快捷键对应表中的图标来打开[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 在快捷键对应表中右键单击，然后选择 "**新建快捷键**"，或选择表底部的空行条目。

1. 从 " **id** " 框中的下拉列表中选择**id** ，或在 " **id** " 框中键入新*id* 。

1. 键入要用作快捷键的*键*，或右键单击并选择 "**下一键类型**" 以设置键组合，或单击 "前往菜单" "**编辑**" > **下一键类型**。

1. 如有必要，请更改**修饰符**和**类型**，然后按**enter**。

> [!NOTE]
> 确保定义的所有快捷键都是唯一的。 可以将多个键组合分配给相同的 ID，但不会产生任何影响，例如， **Ctrl**+**P**和**F8**都可以分配给 ID_PRINT。 但是，分配给多个 ID 的组合键不能正常运行，例如， **Ctrl**+**Z**分配给 ID_SPELL_CHECK 和 ID_THESAURUS。

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>若要从快捷键对应表删除项

1. 通过双击快捷键对应表中的图标来打开[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 选择要删除的项，或在选择时按住**Ctrl**或**Shift**键选择多个项。

1. 右键单击并选择 "**删除**"，或单击 "浏览" "**编辑** > **删除**"。

> [!TIP]
> 还可以按**delete**键删除。

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>将快捷键对应表项移动或复制到另一个资源脚本文件

1. 在两个资源脚本文件中打开快捷键对应表，并选择要移动的项。

1. 从 "**编辑**" 菜单中，选择 "**复制**" 或 "**剪切**"。

1. 选择目标资源脚本文件中的条目，然后从 "**编辑**" 菜单中选择 "**粘贴**"。

> [!NOTE]
> 还可以使用快捷键进行复制和粘贴。

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>更改多个快捷键的属性

1. 通过双击快捷键对应表中的图标来打开[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 按住**Ctrl**键的同时选择每个快捷键，即可选择要更改的快捷键。

1. 中转到 "[属性窗口](/visualstudio/ide/reference/properties-window)"，然后键入所需的值来共享所有所选的快捷键。

> [!NOTE]
> 每个修改值在 "**属性**" 窗口中显示为一个布尔属性。 如果在 "**属性**" 窗口中更改[修改](../windows/accelerator-modifier-property.md)值，则快捷键对应表会将新修饰符视为添加到以前存在的任何修饰符。 因此，如果设置了任何修改值，则需要设置所有修改值，以确保每个加速器共享相同的**修饰符**设置。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
[快捷键](../windows/predefined-accelerator-keys.md)<br/>
