---
title: 快捷键编辑器 （c + +）
ms.date: 11/04/2016
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
ms.openlocfilehash: 5ece5c7e85a3ef59b728474746e9553a751d43c6
ms.sourcegitcommit: bec1480a03e7b4070b469a6c131a69f516bbac70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226340"
---
# <a name="accelerator-editor-c"></a>快捷键编辑器 （c + +）

快捷键对应表是包含一系列加速键 （也称为键盘快捷方式） 的 c + + Windows 资源和与之关联的命令标识符。 一个程序可以拥有多个快捷键对应表。

通常情况下，快捷键用作程序命令的键盘快捷键，也可用于菜单或工具栏。 但是，快捷键对应表可用于为没有关联用户界面对象的命令定义组合键。

可以使用 [类视图](/visualstudio/ide/viewing-the-structure-of-code) 将快捷键命令与代码挂接。

预定义的快捷键的列表，请参阅[预定义快捷键](../windows/predefined-accelerator-keys.md)。

   > [!TIP]
   > 使用时**Accelerator**编辑器中，你可以右击以显示常用命令的快捷菜单。 可用命令取决于指针所指向的内容。

   > [!NOTE]
   > Windows 不允许创建空快捷键对应表。 如果创建的快捷键对应表中没有任何条目，在保存表时会被自动删除。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="accelerator-properties"></a>快捷键属性

可以设置快捷键属性[属性窗口](/visualstudio/ide/reference/properties-window)在任何时间。 此外可以使用**Accelerator**编辑器修改快捷键对应表中的快捷键属性。 使用所做更改**属性**窗口或**Accelerator**编辑器具有相同的结果： 在快捷键对应表中都即时反映编辑。

### <a name="id-property"></a>ID 属性

**ID**属性引用在程序代码中的每个快捷键对应表项。 此条目是当用户按下的加速键或键组合，程序将接收的命令值。 若要使快捷键与菜单项相同，使其 Id 相同 （只要快捷键对应表的 ID 是菜单资源的 ID 相同）。

有三个属性的每个快捷键 ID:**修饰符**属性，**密钥**属性，并且**类型**属性。

#### <a name="modifier-property"></a>Modifier 属性

**修饰符**属性设置控件的快捷键的组合键。

> [!NOTE]
> 在中**属性**窗口中，此属性显示为三个单独**布尔**属性，所有这些可独立控制：**Alt**， **Ctrl**，和**Shift**。

以下是合法的条目**修饰符**快捷键对应表中的属性：

   |值|描述|
   |-----------|-----------------|
   |**无**|用户仅按**密钥**值。 使用此值是最有效地使用 ASCII/ANSI 值 001 026，通过它解释为 ^ A 到 ^ Z (**Ctrl + A**通过**Ctrl + Z**)。|
   |**Alt**|用户必须按**Alt**密钥之前**密钥**值。|
   |**Ctrl**|用户必须按**Ctrl**密钥之前**密钥**值。 与 ASCII 类型无效。|
   |**Shift**|用户必须按**Shift**密钥之前**密钥**值。|
   |**Ctrl+Alt**|用户必须按**Ctrl**密钥和**Alt**密钥之前**密钥**值。 与 ASCII 类型无效。|
   |**Ctrl+Shift**|用户必须按**Ctrl**密钥和**Shift**密钥之前**密钥**值。 与 ASCII 类型无效。|
   |**Alt+Shift**|用户必须按**Alt**密钥和**Shift**密钥之前**密钥**值。 与 ASCII 类型无效。|
   |**Ctrl+Alt+Shift**|用户必须按**Ctrl**， **Alt**，并**Shift**之前**密钥**值。 与 ASCII 类型无效。|

#### <a name="key-property"></a>Key 属性

**密钥**属性设置实际用作快捷键的键。

以下是合法的条目**密钥**快捷键对应表中的属性：

   |值|描述|
   |-----------|-----------------|
   |0 到 255 以十进制格式之间的整数。|值确定是否值视为 ASCII 或 ANSI，如下所示：<br/><br/>-一位数字始终解释为相应的项，而不是作为 ASCII 或 ANSI 值。<br/>值从 1 到 26 的前面加零上, 时被解释为 ^ A 到 ^ Z，表示与按下时的字母表的字母的 ASCII 值**Ctrl**按下键。<br/>-27-32 中的值始终被解释为三位十进制值 027 到 032。<br/>-值从 033 到 255，0 的前面还是不被解释为 ANSI 值。|
   |单个键盘字符。|大写字母 A-Z 或数字 0-9 可以是 ASCII 或虚拟键值;任何其他字符仅为 ASCII。|
   |A-Z 范围内的单个键盘字符 （仅大写的）、 前面插入符号 (^) (例如，^ C)。|与按下时，此选项将进入键的 ASCII 值**Ctrl**按下键。|
   |任何有效的虚拟键标识符。|快捷键对应表中的下拉列表密钥框包含一组标准的虚拟键标识符。|

> [!NOTE]
> 当输入 ASCII 值，被限制修饰符属性选项。 唯一控件可用的密钥使用的是**Alt**密钥。

> [!TIP]
> 定义快捷键另一种方法是右键单击一项或多个快捷键对应表中的项，请选择**键入的下一个密钥**从快捷菜单，然后在键盘上按任何键或组合键。 **键入的下一步键**命令也会提供**编辑**菜单。

#### <a name="type-property"></a>Type 属性

**类型**属性确定与快捷键 ID 相关联的快捷键组合被解释为 ASCII/ANSI 密钥值或虚拟键 (VIRTKEY) 组合。

- 如果**类型**属性是 ASCII**修饰符**属性只能`None`或`Alt`，也可以使用快捷键**Ctrl**密钥 （指定的前面使用的密钥`^`)。

- 如果**类型**属性是 VIRTKEY 的任意组合`Modifier`和`Key`值是否有效。

> [!NOTE]
> 如果希望快捷键对应表中输入一个值，并将值作为 ASCII/ANSI，只需单击处理**类型**表并从下拉列表中选择 ASCII 中的条目。 但是，如果您使用**键入的下一步键**命令 (**编辑**菜单) 来指定`Key`，则必须更改**类型**属性从 VIRTKEY 为 ASCII *之前*输入`Key`代码。

## <a name="accelerator-tables"></a>快捷键对应表

在 c + + 项目中，可以直接使用就地编辑中编辑快捷键对应表**Accelerator**编辑器。

下面的过程涉及到使用标准属性页，但是，就地编辑和属性页面方法都具有相同的结果。 所做的更改使用属性页或使用就地编辑将立即反映在快捷键对应表中。

> [!NOTE]
> 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

### <a name="to-edit-in-an-accelerator-table"></a>在快捷键对应表中编辑

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

1. 在表中选择一个条目，并选择以激活就地编辑。

1. 从下拉组合框中进行选择或就地输入以进行更改。

   - 有关**ID**，从选择列表或输入以进行编辑。

   - 有关**修饰符**，从列表中选择。

   - 有关**密钥**，从选择列表或输入以进行编辑。

   - 有关**类型**，选择**ASCII**或**VIRTKEY**从列表中。

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>在打开的快捷键对应表中查找项

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

1. 选择列标题可以按字母顺序排序的列的内容。 例如，选择**ID**快捷键对应表中按字母顺序显示所有 Id。

然后，可以浏览列表并找到该项。

### <a name="to-add-an-entry-to-an-accelerator-table"></a>向快捷键对应表添加项

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

1. 在快捷键对应表中右键单击并选择**新的加速器**从快捷菜单上或选择表底部的空行项。

1. 选择**ID**从 ID 中的下拉列表框或键入中的新 ID **ID**框。

1. 类型**键**你想要用作快捷键或右键单击并选择**键入的下一步键**从快捷菜单来设置组合键 (**键入的下一个密钥**命令是也可从**编辑**菜单)。

1. 更改**修饰符**并**类型**，如果有必要。

1. 按 **Enter**。

   > [!NOTE]
   > 确保定义的所有快捷键都是唯一的。 您可以将多种组合键分配给相同 ID 而产生任何不良影响，例如， **Ctrl** + **P**并**F8**可以同时分配给 ID_PRINT。 但是，具有分配给多个 ID 会无法正常工作，例如，组合键**Ctrl** + **Z**分配给 ID_SPELL_CHECK 和 ID_THESAURUS。

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>若要从快捷键对应表删除项

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

1. 选择要删除的项。 (按住**Ctrl**或**Shift**键并选择以选择多个条目。)

1. 右键单击并选择**删除**从快捷菜单 (或选择**删除**从**编辑**菜单)。

> [!TIP]
> 删除的快捷方式是按**删除**密钥。

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>将快捷键对应表项移动或复制到另一个资源脚本文件

1. 在这两个资源脚本文件中打开快捷键对应表。

1. 选择要移动的项。

1. 从**编辑**菜单中，选择**副本**或**剪切**。

1. 在目标资源脚本文件中选择一个项。

1. 从**编辑**菜单中，选择**粘贴**。

   > [!NOTE]
   > 还可以使用快捷键进行复制和粘贴。

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>若要更改多个快捷键的属性

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

1. 选择你想要更改通过按下的快捷键**Ctrl**选择每个键。

1. 转到[属性窗口](/visualstudio/ide/reference/properties-window)和中所需的所选的加速器共享所有的值类型。

   > [!NOTE]
   > 每个修饰符值显示为一个布尔值属性中**属性**窗口。 如果您更改[修饰符](../windows/accelerator-modifier-property.md)中的值**属性**窗口中，快捷键对应表视为新修饰符对先前已存在任何修饰符的补充。 因此，如果设置任何修饰符的值，您将需要设置它们以确保每个快捷键共享相同的所有**修饰符**设置。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)

[在快捷键对应表中编辑](../windows/editing-in-an-accelerator-table.md)<br/>
[预定义快捷键](../windows/predefined-accelerator-keys.md)<br/>