---
title: 字符串编辑器 （C++）
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
ms.openlocfilehash: b0fb077752cf1912e07175c68cdc8acfe758b0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370243"
---
# <a name="string-editor-c"></a>字符串编辑器 （C++）

字符串表是 Windows 资源，其中包含应用程序的所有字符串的 ID、值和标题的列表。 例如，状态栏提示位于字符串表中。

开发应用程序时，可以具有多个字符串表 — 每种语言或条件使用一个。 但是，可执行模块只有一个字符串表。 如果将表放入不同 DLL 中，则正在运行的应用程序可以引用多个字符串表。

通过字符串表可以更加轻松地将应用程序本地化为不同语言。 如果所有字符串都处于字符串表中，则可以通过翻译字符串（和其他资源）来本地化应用程序，而无需更改源代码。 这种情况比手动查找和替换源文件中的各种字符串更可取。

> [!NOTE]
> Windows 不允许创建空字符串表。 如果创建的字符串表中没有任何条目，则它在保存资源文件时会自动删除。

## <a name="how-to"></a>操作方式

**字符串编辑器**使您能够：

### <a name="to-find-a-string-resource-in-the-string-table"></a>在字符串表中查找字符串资源

1. 通过双击资源[视图中](how-to-create-a-resource-script-file.md#create-resources)的图标打开字符串表。

1. 转到菜单 **"编辑** > **查找和替换**"并选择 **"查找**"。

1. 在"**查找什么"** 框中，从下拉列表中选择以前的搜索字符串，或键入要查找的字符串的标题文本或资源标识符。

1. 选择任何 **"查找"** 选项，然后选择 **"查找下一步**"。

> [!TIP]
> 要在搜索文件时使用[正则表达式](/visualstudio/ide/using-regular-expressions-in-visual-studio)，请使用 **"编辑"** 菜单**中的"在文件中查找"** 命令。
>
> 键入正则表达式以匹配模式或选择"**查找什么"** 框右侧的按钮以显示常规搜索表达式的列表。 从此列表中选择表达式时，该表达式将替换为"**查找什么"** 框中的搜索文本。
>
> 如果使用正则表达式，请确保选择了 **"使用：正则表达式**"复选框。

### <a name="to-add-or-delete-a-string-resource"></a>添加或删除字符串资源

您可以使用**字符串编辑器**快速将条目插入或删除到字符串表中。 新字符串放在表的末尾，并给出下一个可用标识符。 您可以根据需要在["属性"窗口中](/visualstudio/ide/reference/properties-window)编辑**ID、****值**或**标题**属性。

**字符串编辑器**确保不使用已在使用的 ID。 如果选择已在使用的 ID，**字符串编辑器**将通知您，然后分配通用的唯一 ID，例如`IDS_STRING58113`。

#### <a name="to-add-a-string-table-entry"></a>添加字符串表条目

1. 通过双击资源[视图中](how-to-create-a-resource-script-file.md#create-resources)的图标打开字符串表。

1. 右键单击字符串表并选择 **"新建字符串**"。

1. 在**字符串编辑器**中，从**ID**下拉列表中选择**ID**或直接键入正确的*ID。*

1. 如有必要，编辑**值**。

1. 键入**标题**的条目 。

   > [!NOTE]
   > Windows 字符串表中不允许使用空字符串。 如果在字符串表中创建一个空字符串的条目，您将收到一条消息，要求您**为此表条目输入字符串**。

#### <a name="to-delete-a-string-table-entry"></a>删除字符串表条目

选择要删除的条目，并执行以下操作之一：

- 转到菜单 **"编辑** > **删除**"。

- 右键单击要删除的字符串，然后选择 **"删除**"。

- 按 **"删除**"键。

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>将字符串从一个资源脚本文件移动到另一个资源脚本文件

1. [打开两个 .rc 文件中的字符串表](../windows/how-to-create-a-resource-script-file.md)。

1. 右键单击字符串以移动并选择 **"剪切**"。

1. 将光标放在目标**字符串编辑器**窗口中。

1. 在要移动到*的 .rc*文件中，右键单击并选择 **"粘贴**"。

> [!NOTE]
> 如果移动字符串的**ID**或**值**与目标文件中的现有**ID**或**值**冲突，则该**ID**或移动字符串**的值**将发生更改。

### <a name="to-change-the-properties-of-a-string-resource"></a>更改字符串资源的属性

可以使用就地编辑来更改**ID、****值**和**标题**属性。

> [!NOTE]
> 您还可以在["属性"窗口中](/visualstudio/ide/reference/properties-window)编辑字符串的属性。

#### <a name="to-change-a-string-or-its-identifier"></a>更改字符串或其标识符

1. 通过双击资源[视图中](how-to-create-a-resource-script-file.md#create-resources)的图标打开字符串表。

1. 选择要编辑的字符串，然后双击**ID、****值**或**标题**列，然后您可以：

   - 从**ID**下拉列表中选择**ID，** 或直接键入正确的*ID。*

   - 在 **"值"** 列中键入其他数字。

   - 在 **"标题"** 列中键入编辑。

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>更改多个字符串资源的标题属性

1. 通过双击资源[视图中](how-to-create-a-resource-script-file.md#create-resources)的图标打开字符串表。

1. 在选择每个字符串时按住**Ctrl**键，选择要更改的字符串。

1. 在["属性"窗口中](/visualstudio/ide/reference/properties-window)，为要更改的属性键入新值。

1. 按 Enter****。

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>向字符串资源添加格式或特殊字符

1. 通过双击资源[视图中](how-to-create-a-resource-script-file.md#create-resources)的图标打开字符串表。

1. 选择要修改的字符串。

1. 在["属性"窗口中](/visualstudio/ide/reference/properties-window)，将下面列出的任何标准转义序列添加到 **"标题"** 框中的文本，然后按**Enter**。

   |为了得到这个...|键入此...|
   |-----------------|---------------|
   | 新建行 | \\n |
   | 回车符 | \\R |
   | Tab | \\t |
   | 反斜杠 (\\) | \\\\ |
   | ASCII 字符 | \\dd（八度表示法） |
   | 警报（铃） | \\a |

   > [!NOTE]
   > **字符串编辑器**不支持完整的转义 ASCI 字符集。 您只能使用上面列出的那些。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[资源编辑器](../windows/resource-editors.md)
[字符串](/windows/win32/menurc/strings)<br/>
[关于字符串](/windows/win32/menurc/about-strings)<br/>
[自定义窗口布局](/visualstudio/ide/customizing-window-layouts-in-visual-studio)
