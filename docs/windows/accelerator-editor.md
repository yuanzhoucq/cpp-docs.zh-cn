---
title: 快捷键编辑器 （c + +）
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
ms.openlocfilehash: f5ae9880719a3a8b799ea8deb751b6f0a85542bd
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041119"
---
# <a name="accelerator-editor-c"></a>快捷键编辑器 （c + +）

快捷键对应表是 c + + Windows 资源，其中包含加速键，称为键盘快捷方式，并与之关联的命令标识符的列表。 一个程序可以拥有多个快捷键对应表。

通常情况下，快捷键用作程序命令的键盘快捷键，也可用于菜单或工具栏。 但是，快捷键对应表可用于为没有关联用户界面对象的命令定义组合键。

> [!TIP]
> 使用时**快捷键编辑器**，右键单击以显示快捷菜单的常见命令。 可用命令取决于指针所指向的内容。

可以使用 [类视图](/visualstudio/ide/viewing-the-structure-of-code) 将快捷键命令与代码挂接。 预定义的快捷键的列表，请参阅[快捷键](../windows/predefined-accelerator-keys.md)。

> [!NOTE]
> Windows 不允许创建空快捷键对应表。 如果创建的快捷键对应表中没有任何条目，在保存表时会被自动删除。

## <a name="accelerator-properties"></a>快捷键属性

可以设置快捷键属性[属性窗口](/visualstudio/ide/reference/properties-window)在任何时间。 此外可以使用**快捷键编辑器**修改快捷键对应表中的快捷键属性。 使用所做更改**属性**窗口或**快捷键编辑器**具有相同的结果，在快捷键对应表中都即时反映编辑。

**ID**属性引用在程序代码中的每个快捷键对应表项。 此条目是当用户按下的加速键或键组合该程序将接收的命令值。 若要使快捷键与菜单项相同，请**ID**相同，因此长达**ID** accelerator 的表是与相同**ID**菜单资源。

每个加速器**ID**具有三个属性：**修饰符**，**密钥**，和**类型**

**修饰符**属性设置控件的快捷键的组合键。

> [!NOTE]
> 在中**属性**窗口中，**修饰符**属性显示为三个单独**布尔**属性，所有这些可独立控制：**Alt**， **Ctrl**，和**Shift**。

以下是合法的条目**修饰符**快捷键对应表中的属性：

   |值|描述|
   |-----------|-----------------|
   |**None**|用户仅按**密钥**值。<br/><br/>使用此值是最有效地使用 ASCII/ANSI 值 001 026，通过它解释为 ^ A 到 ^ Z (**Ctrl + A**通过**Ctrl + Z**)。|
   |**Alt**|用户必须按**Alt**之前**密钥**值。|
   |**Ctrl**|用户必须按**Ctrl**之前**密钥**值，与 ASCII 类型无效。|
   |**移位**|用户必须按**Shift**之前**密钥**值。|
   |**Ctrl+Alt**|用户必须按**Ctrl**并**Alt**之前**密钥**值，与 ASCII 类型无效。|
   |**Ctrl+Shift**|用户必须按**Ctrl**并**Shift**之前**密钥**值，与 ASCII 类型无效。|
   |**Alt+Shift**|用户必须按**Alt**并**Shift**之前**密钥**值，与 ASCII 类型无效。|
   |**Ctrl+Alt+Shift**|用户必须按**Ctrl**， **Alt**，并**Shift**之前**密钥**值，与 ASCII 类型无效。|

**密钥**属性设置实际用作快捷键的键。

以下是合法的条目**密钥**快捷键对应表中的属性：

   |值|描述|
   |-----------|-----------------|
   |0 到 255 以十进制格式之间的整数。|值确定是否值视为 ASCII 或 ANSI，如下所示：<br/><br/>   -一位数字始终解释为相应的项，而不是作为 ASCII 或 ANSI 值。<br/>   值从 1 到 26 的前面加零上, 时被解释为 ^ A 到 ^ Z，表示与按下时的字母表的字母的 ASCII 值**Ctrl**按下键。<br/>   -27-32 中的值始终被解释为三位十进制值 027 到 032。<br/>   -值从 033 到 255，0 的前面还是不被解释为 ANSI 值。|
   |单个键盘字符。|大写字母 A-Z 或数字 0-9 可以是 ASCII 或虚拟键值。 任何其他字符仅为 ASCII。|
   |A-Z 范围内的单个键盘字符 （仅为大写），例如，前面插入符号 (^) ^ c。|与按下时，此选项将进入键的 ASCII 值**Ctrl**按下键。|
   |任何有效的虚拟键标识符。|下拉列表**密钥**快捷键对应表中的框包含一组标准的虚拟键标识符。|

> [!NOTE]
> 输入 ASCII 值时**修饰符**属性选项受限制。 唯一控件可用的密钥使用的是**Alt**密钥。

> [!TIP]
> 若要定义一个加速键的快捷方式是右键单击条目或快捷键对应表中的多个条目，然后选择**键入的下一个密钥**键盘上按任意键或组合键。
>
> 这**键入的下一步键**命令也会提供**编辑**菜单。

**类型**属性确定是否与快捷键相关联的快捷键组合**ID**被解释为 ASCII/ANSI 密钥值或虚拟键 (VIRTKEY) 组合。

- 如果**类型**属性是**ASCII**，则**修饰符**属性只能是`None`或`Alt`，也可以使用accelerator**Ctrl**密钥，指定的前面使用的密钥`^`。

- 如果**类型**属性是**VIRTKEY**的任意组合**修饰符**并**密钥**值是否有效。

> [!NOTE]
> 如果希望快捷键对应表中输入一个值，并将值作为 ASCII/ANSI，选择处理**类型**在表中，选择项**ASCII**从下拉列表中。 但是，如果您使用**键入的下一个键**命令**编辑**菜单指定**密钥**，则必须更改**类型**属性从**VIRTKEY**到**ASCII** *之前*输入**密钥**代码。

## <a name="accelerator-tables"></a>快捷键对应表

在 c + + 项目中，可以直接使用就地编辑中编辑快捷键对应表**快捷键编辑器**。

下面的过程涉及到使用标准属性页，但是，就地编辑和属性页面方法都具有相同的结果。 所做的更改使用属性页或使用就地编辑将立即反映在快捷键对应表中。

### <a name="to-edit-in-an-accelerator-table"></a>在快捷键对应表中编辑

1. 通过双击中对应的图标打开快捷键对应表[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 在表中选择一个条目，并选择以激活就地编辑。

1. 从下拉组合框中选择或就地输入以进行更改：

   - 有关**ID**，从选择列表或输入以进行编辑。

   - 有关**修饰符**，从列表中选择。

   - 有关**密钥**，从选择列表或输入以进行编辑。

   - 有关**类型**，选择**ASCII**或**VIRTKEY**从列表中。

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>在打开的快捷键对应表中查找项

1. 通过双击中对应的图标打开快捷键对应表[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 选择列标题可以按字母顺序排序的列的内容。 例如，选择**ID**快捷键对应表中按字母顺序显示所有 Id。

   然后，可以浏览列表并找到该项。

### <a name="to-add-an-entry-to-an-accelerator-table"></a>向快捷键对应表添加项

1. 通过双击中对应的图标打开快捷键对应表[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 在快捷键对应表中右键单击并选择**新的加速器**，或选择表底部的空行项。

1. 选择**ID**从下拉列表中**ID**框中，或键入一个新*ID*中**ID**框。

1. 类型*键*你想要用作快捷键，或右键单击，然后选择**键入的下一步键**若要设置的键的组合，或转到菜单**编辑** >  **键入下一个键**。

1. 更改**修饰符**并**类型**，如有必要，然后按**Enter**。

> [!NOTE]
> 确保定义的所有快捷键都是唯一的。 您可以将多种组合键分配给相同 ID 而产生任何不良影响，例如， **Ctrl**+**P**并**F8**可以同时分配给 ID_PRINT。 但是，具有分配给多个 ID 不会顺利执行，例如，组合键**Ctrl**+**Z**分配给 ID_SPELL_CHECK 和 ID_THESAURUS。

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>若要从快捷键对应表删除项

1. 通过双击中对应的图标打开快捷键对应表[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 选择你想要删除，或按下的条目**Ctrl**或**Shift**键并选择以选择多个条目。

1. 右键单击并选择**删除**，或转到菜单**编辑** > **删除**。

> [!TIP]
> 此外可以按**删除**若要删除的密钥。

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>将快捷键对应表项移动或复制到另一个资源脚本文件

1. 在这两个资源脚本文件中打开快捷键对应表并选择你想要移动的项。

1. 从**编辑**菜单中，选择**副本**或**剪切**。

1. 选择一个条目，在目标资源脚本文件，并从**编辑**菜单中，选择**粘贴**。

> [!NOTE]
> 还可以使用快捷键进行复制和粘贴。

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>若要更改多个快捷键的属性

1. 通过双击中对应的图标打开快捷键对应表[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 选择你想要更改通过按下的快捷键**Ctrl**选择每个键。

1. 转到[属性窗口](/visualstudio/ide/reference/properties-window)和中所需的所选的加速器共享所有的值类型。

> [!NOTE]
> 每个修饰符值显示为一个布尔值属性中**属性**窗口。 如果您更改[修饰符](../windows/accelerator-modifier-property.md)中的值**属性**窗口中，快捷键对应表视为新修饰符对先前已存在任何修饰符的补充。 因此，如果设置任何修饰符的值，您需要设置它们以确保每个快捷键共享相同的所有**修饰符**设置。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
[快捷键](../windows/predefined-accelerator-keys.md)<br/>