---
title: 菜单命令 (C++)
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
ms.openlocfilehash: c9abf46907c473d4cf6d9e945038f70aa75bfc48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376713"
---
# <a name="menu-commands-c"></a>菜单命令 (C++)

根据组织以下信息**菜单**中显示的属性[属性窗口](/visualstudio/ide/reference/properties-window)选择菜单命令时。 这些字母顺序列出，尽管**属性**窗口还可以按类别查看这些属性。

|属性|描述|
|--------------|-----------------|
|**中断**|可以是下列值之一：<br/>  - **无**:不是中断。 这是默认设置。<br/>  - **列**:对于静态菜单，此值将菜单命令置于新行。<br/>      对于弹出菜单，此值将菜单命令放置在新列，列之间无分隔线。<br/>      设置此属性仅会影响运行时的菜单的外观，不会影响菜单编辑器中的外观。<br />   - **栏**:与相同**列**除外，对于弹出菜单，此值的新列与旧列分隔有一条垂直线。<br/>      设置此属性不是在将影响仅在运行时，菜单的外观**菜单编辑器**。|
|**标题**|标记菜单命令（菜单名）的文本。 若要使一个菜单命令的标题中的字母之一成为助记键，请在它前面加上 & 号 (&)。|
|**已选中**|如果 **，则返回 True**，则最初检查菜单命令。 类型：**Bool**。 默认：**False**。|
|**启用**|如果为 **False**，则菜单项被禁用。|
|**灰显**|如果 **，则返回 True**，则菜单命令是最初显示为灰色且处于非活动状态。 类型：**Bool**。 默认：**False**。|
|**帮助**|将菜单项对齐到右侧。 默认：**False**。<br/><br/>例如， **帮助** 菜单命令在所有 Windows 应用程序中始终位于右侧。 如果在一个菜单项上设置此属性，则该项将出现在菜单的最右边和最末尾。 适用于顶级项。|
|**ID**|在头文件中定义的符号。 类型：**符号**，**整数**，或**带引号的字符串**。<br/><br/>你可以使用通常在任何编辑器中均可用的任何符号，即使 [属性窗口](/visualstudio/ide/reference/properties-window) 不提供可供你从中进行选择的下拉列表。|
|**弹出项**|如果 **，则返回 True**，菜单命令是一个弹出菜单。 类型：**Bool**。 默认：**True**对于顶级菜单在菜单栏上，否则为**False**。|
|**提示**|包含突出显示此菜单命令时要在状态栏中显示的文本。 文本放在具有与菜单命令相同的标识符的字符串表中。<br/><br/>此属性可用于任何类型的项目，但运行时功能是 MFC 专用的。|
|**从右到左对齐**|在运行时右对齐菜单栏上的菜单命令。 类型：**Bool**。 默认：**False**。|
|**从右到左的顺序**|界面被本地化为任何从右到左读取的语言（例如希伯来语或阿拉伯语）时允许菜单命令按从右到左显示。|
|**分隔符**|如果 **，则返回 True**，菜单命令是一个分隔符。 类型：**Bool**。 默认：**False**。|

## <a name="associate-menu-commands"></a>菜单命令相关联

你经常希望某一菜单命令和某一键盘组合可以发出相同的程序命令。 通过使用在发出相同的命令**菜单编辑器**到菜单命令和应用程序的快捷键对应表中的条目分配相同的资源标识符。 接着你可以编辑该菜单命令的 [标题](../windows/menu-command-properties.md) ，以显示快捷键的名称。

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>将菜单命令与快捷键关联

1. 在中**菜单编辑器**，选择所需的菜单命令。

1. 在[“属性窗口”](/visualstudio/ide/reference/properties-window)中，向 **“标题”** 属性添加快捷键的名称：

   - 在菜单标题后面，输入制表符 (\t) 的转义序列，以使所有菜单的快捷键都左对齐。

   - 键入的修改键名称 (**Ctrl**， **Alt**，或**Shift**) 后跟一个加号 (**+**) 和名称、 字母，或其他键的符号。

   例如，若要将分配**Ctrl**+**O**到**打开**命令**文件**菜单中，修改的菜单命令**标题**，使其类似于以下文本：

   ```
   &Open...\tCtrl+O
   ```

   中的菜单命令**菜单编辑器**更新以反映新的标题，并在您键入。

1. 在[“快捷键”](../windows/adding-an-entry-to-an-accelerator-table.md) 编辑器中 **创建快捷键对应表条目** 并向它分配与菜单命令相同的标识符。 使用你认为易于记住的组合键。

MFC 应用程序可以为每个用户可能选择的菜单命令显示说明性文本。 通过将文本字符串分配给每个菜单命令使用显示的说明性文本**Prompt**属性中的**属性**窗口。 如果 [字符串表](../windows/string-editor.md) 中有一个字符串，其 ID 与命令相同，则当用户悬停在菜单项上方时，MFC 应用程序将在运行的应用程序的状态栏中自动显示此字符串资源。

- 若要将菜单命令与状态栏 MFC 应用程序中的文本字符串中**菜单编辑器**，选择菜单命令。 在 [属性窗口](/visualstudio/ide/reference/properties-window)的 **“提示”** 框中键入关联的状态栏文本。

在C++项目中，您可以向菜单和菜单命令分配访问键 （使用户可以用键盘选择菜单的助记键）。

- 若要向菜单命令分配访问 （快捷） 键，输入与号 (`&`) 中的菜单名称或命令名称以该字母指定为相应的访问密钥的某个字母前。 

   例如，"& 文件"集**Alt**+**F**作为的快捷键**文件**为 Microsoft Windows 编写应用程序中的菜单。

   菜单项会提供一个可见提示，指出已向一个字母分配了快捷键。 与号后面的字母在出现时会带有下划线（取决于操作系统）。

> [!NOTE]
> 请确保菜单上的所有访问键都是唯一的通过右键单击菜单，然后选择**检查助记键**。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[菜单编辑器](../windows/menu-editor.md)<br/>

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->