---
title: 字符串编辑器 (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.string.F1
- vc.editors.string
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
- strings [C++], searching
- strings [C++]
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: 47d5835356863383b32baffc4475e01a652e9856
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037180"
---
# <a name="string-editor-c"></a>字符串编辑器 (C++)

字符串表是 Windows 资源，其中包含应用程序的所有字符串的 ID、值和标题的列表。 例如，状态栏提示位于字符串表中。

开发应用程序时，可以具有多个字符串表 — 每种语言或条件使用一个。 但是，可执行模块只有一个字符串表。 如果将表放入不同 DLL 中，则正在运行的应用程序可以引用多个字符串表。

通过字符串表可以更加轻松地将应用程序本地化为不同语言。 如果所有字符串都处于字符串表中，则可以通过翻译字符串（和其他资源）来本地化应用程序，而无需更改源代码。 这种情况下是比手动查找和替换源文件中的各种字符串更加理想。

> [!NOTE]
> Windows 不允许空字符串表的创建。 如果创建的字符串表中没有任何条目，则它在保存资源文件时会自动删除。

## <a name="how-to"></a>操作说明

**字符串编辑器**，可以：

### <a name="to-find-a-string-resource-in-the-string-table"></a>若要在字符串表中查找的字符串资源

1. 通过双击中对应的图标打开字符串表[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 转到菜单**编辑** > **查找和替换**，然后选择**查找**。

1. 在中**查找内容**框中，从下拉列表中，选择以前的搜索字符串或键入想要查找的字符串的标题文本或资源标识符。

1. 选择任一**查找**选项，然后选择**查找下一个**。

> [!TIP]
> 若要使用[正则表达式](/visualstudio/ide/using-regular-expressions-in-visual-studio)在搜索文件时，使用**在文件中查找**命令，在**编辑**菜单。
>
> 键入要与模式匹配，或选择右侧的按钮的正则表达式**查找内容**框，以显示搜索正则表达式的列表。 当从此列表中选择一个表达式时，它将替换中的搜索文本**查找内容**框。
>
> 如果使用正则表达式，请确保**使用：正则表达式**复选框处于选中状态。

### <a name="to-add-or-delete-a-string-resource"></a>若要添加或删除字符串资源

您可以快速插入或删除到字符串表使用的条目**字符串编辑器**。 新字符串放在表的末尾，并将给定的下一步提供标识符。 您可以编辑**ID**，**值**，或**标题**中的属性[属性窗口](/visualstudio/ide/reference/properties-window)根据需要。

**字符串编辑器**可确保不使用已在使用的 ID。 如果您选择 ID 已在使用中，**字符串编辑器**将通知你，然后分配一个通用的唯一 ID，例如`IDS_STRING58113`。

#### <a name="to-add-a-string-table-entry"></a>若要添加的字符串表项

1. 通过双击中对应的图标打开字符串表[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 字符串表中右键单击并选择**新的字符串**。

1. 在中**字符串编辑器**，选择**ID**从**ID**下拉列表或类型*ID*直接在位置中。

1. 编辑**值**，如果有必要。

1. 键入的条目**标题**。

   > [!NOTE]
   > 在 Windows 字符串表中不允许 null 字符串。 如果您是一个 null 字符串的字符串表中创建一个条目，将收到一条消息询问你**请输入该表项字符串**。

#### <a name="to-delete-a-string-table-entry"></a>若要删除的字符串表项

选择你想要删除并执行以下任一的项：

- 转到菜单**编辑** > **删除**。

- 右键单击要删除和选择的字符串**删除**。

- 按**删除**密钥。

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>若要将字符串从一个资源脚本文件移动到另一个

1. [在这两个.rc 文件中打开字符串表](../windows/how-to-create-a-resource-script-file.md)。

1. 右键单击要移动和选择的字符串**剪切**。

1. 将光标放在目标**字符串编辑器**窗口。

1. 在中 *.rc*想要移动字符串，用鼠标右键单击并选择的文件**粘贴**。

> [!NOTE]
> 如果**ID**或**值**与某个现有的移动的字符串冲突**ID**或者**值**在目标文件中，任一该**ID**或**值**的更改已移动的字符串。

### <a name="to-change-the-properties-of-a-string-resource"></a>若要更改的字符串资源的属性

可以使用就地编辑来更改**ID**，**值**，并**标题**属性。

> [!NOTE]
>  此外可以编辑字符串的属性中[属性窗口](/visualstudio/ide/reference/properties-window)。

#### <a name="to-change-a-string-or-its-identifier"></a>若要更改字符串或其标识符

1. 通过双击中对应的图标打开字符串表[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 选择你想要编辑，并双击的字符串**ID**，**值**，或**标题**列，则你可以：

   - 选择**ID**从**ID**下拉列表中或类型*ID*直接在位置中。

   - 键入在不同的数字**值**列。

   - 键入中的编辑**标题**列。

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>若要更改多个字符串资源的标题属性

1. 通过双击中对应的图标打开字符串表[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 选择你想要通过按下更改的字符串**Ctrl**选择每个键。

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，键入你想要更改的属性的新值。

1. 按 **Enter**。

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>若要将格式设置或特殊字符添加到字符串资源

1. 通过双击中对应的图标打开字符串表[资源视图](how-to-create-a-resource-script-file.md#create-resources)。

1. 选择你想要修改的字符串。

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，添加任何标准的转义序列中的文本到下列**标题**框，然后按**Enter**。

   |若要获取此信息...|键入此...|
   |-----------------|---------------|
   | 换行 | \\n |
   | 回车 | \\r |
   | Tab | \\t |
   | 反斜杠 (\\) | \\\\ |
   | ASCII 字符 | \\ddd （八进制表示法） |
   | 警报 （响铃） | \\a |

   > [!NOTE]
   > **字符串编辑器**不支持转义 ASCI 字符的完整集。 您只能使用上面所列。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)
<!--
[Strings](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[About Strings](/windows/desktop/menurc/about-strings)<br/>
[Customizing window layouts](/visualstudio/ide/customizing-window-layouts-in-visual-studio)-->