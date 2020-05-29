---
title: 菜单命令（C++）
ms.date: 02/15/2019
helpviewer_keywords:
- menu items, properties
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
- status bars [C++], associating menu items
- menus [C++], status bar text
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
ms.openlocfilehash: 33b1260d088008a94d935f7e4fd7c18b0dd249e3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167935"
---
# <a name="menu-commands-c"></a>菜单命令（C++）

下面的信息根据选择菜单命令时 "[属性" 窗口](/visualstudio/ide/reference/properties-window)中显示的**菜单**属性进行组织。 尽管 "**属性**" 窗口还允许按类别查看这些属性，但它们按字母顺序列出。

|Property|描述|
|--------------|-----------------|
|**中断**|可以是下列值之一：<br/>  **无**- ：无中断。 这是默认设置。<br/>  - **列**：对于静态菜单，此值将菜单命令放置在新行上。<br/>      对于弹出菜单，此值将菜单命令放置在新列，列之间无分隔线。<br/>      设置此属性仅会影响运行时的菜单的外观，不会影响菜单编辑器中的外观。<br />   - **栏**：与**列**相同，但对于弹出菜单，此值将新列与旧列分隔开来。<br/>      设置此属性只会影响运行时的菜单的外观，而不会影响**菜单编辑器**中的外观。|
|**标题**|标记菜单命令（菜单名）的文本。 若要使一个菜单命令的标题中的字母之一成为助记键，请在它前面加上 & 号 (&)。|
|**已选中**|如果**为 True**，则最初检查菜单命令。 键入：**布尔**值。 默认：**False**。|
|**启用**|如果为 **False**，则菜单项被禁用。|
|**灰显**|如果**为 True**，则菜单命令最初显示为灰色且处于非活动状态。 键入：**布尔**值。 默认：**False**。|
|**帮助**|将菜单项对齐到右侧。 默认：**False**。<br/><br/>例如， **帮助** 菜单命令在所有 Windows 应用程序中始终位于右侧。 如果在一个菜单项上设置此属性，则该项将出现在菜单的最右边和最末尾。 适用于顶级项。|
|**ID**|在头文件中定义的符号。 键入：**符号**、**整数**或**带引号的字符串**。<br/><br/>你可以使用通常在任何编辑器中均可用的任何符号，即使 [属性窗口](/visualstudio/ide/reference/properties-window) 不提供可供你从中进行选择的下拉列表。|
|**弹出项**|如果**为 True**，则菜单命令是一个弹出菜单。 键入：**布尔**值。 默认：对于菜单栏上的顶级菜单为**True** ; 否则为**False**。|
|**提示**|包含突出显示此菜单命令时要在状态栏中显示的文本。 文本放在具有与菜单命令相同的标识符的字符串表中。<br/><br/>此属性可用于任何类型的项目，但运行时功能是 MFC 专用的。|
|**从右到左对齐**|在运行时右对齐菜单栏上的菜单命令。 键入：**布尔**值。 默认：**False**。|
|**从右到左的顺序**|界面被本地化为任何从右到左读取的语言（例如希伯来语或阿拉伯语）时允许菜单命令按从右到左显示。|
|**Separator**|如果**为 True**，则菜单命令是一个分隔符。 键入：**布尔**值。 默认：**False**。|

## <a name="associate-menu-commands"></a>关联菜单命令

你经常希望某一菜单命令和某一键盘组合可以发出相同的程序命令。 使用**菜单编辑器**向菜单命令和应用程序快捷键对应表中的条目分配相同的资源标识符。 接着你可以编辑该菜单命令的 [标题](../windows/menu-command-properties.md) ，以显示快捷键的名称。

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>将菜单命令与快捷键关联

1. 在**菜单编辑器**中，选择所需菜单命令。

1. 在[“属性窗口”](/visualstudio/ide/reference/properties-window)中，向 **“标题”** 属性添加快捷键的名称：

   - 在菜单标题后面，输入制表符 (\t) 的转义序列，以使所有菜单的快捷键都左对齐。

   - 键入修改键的名称（**Ctrl**、 **Alt**或**Shift**），后跟一个加号（ **+** ）以及其他键的名称、字母或符号。

   例如，若要为 "**文件**" 菜单上的 "**打开**" 命令分配**Ctrl**+**O** ，请修改菜单命令的**标题**，使其类似于以下文本：

   ```
   &Open...\tCtrl+O
   ```

   当你键入时，**菜单编辑器**中的菜单命令将更新以反映新标题。

1. 在[“快捷键”](../windows/adding-an-entry-to-an-accelerator-table.md) 编辑器中 **创建快捷键对应表条目** 并向它分配与菜单命令相同的标识符。 使用你认为易于记住的组合键。

MFC 应用程序可以为用户可能选择的每个菜单命令显示说明性文本。 使用 "**属性**" 窗口中的 "**提示**" 属性将文本字符串分配给每个菜单命令显示说明性文本。 如果 [字符串表](../windows/string-editor.md) 中有一个字符串，其 ID 与命令相同，则当用户悬停在菜单项上方时，MFC 应用程序将在运行的应用程序的状态栏中自动显示此字符串资源。

- 若要在 MFC 应用程序中将菜单命令与状态栏文本字符串相关联，请在**菜单编辑器**中选择菜单命令。 在 [属性窗口](/visualstudio/ide/reference/properties-window)的 **“提示”** 框中键入关联的状态栏文本。

在C++项目中，可以将访问键（允许用户使用键盘选择菜单的助记键）分配给菜单和菜单命令。

- 若要向菜单命令分配访问（快捷）键，请在菜单名称或命令名称中的某个字母前键入与号（`&`），以将该字母指定为对应的访问键。

   例如，在为 Microsoft Windows 编写的应用程序中，"& 文件" 将**Alt**+**F**设置为 "**文件**" 菜单的快捷键。

   菜单项会提供一个可见提示，指出已向一个字母分配了快捷键。 与号后面的字母在出现时会带有下划线（取决于操作系统）。

> [!NOTE]
> 右键单击菜单并选择 "**检查助记**键"，确保菜单上的所有访问键都是唯一的。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[菜单编辑器](../windows/menu-editor.md)

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->
