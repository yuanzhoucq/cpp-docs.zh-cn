---
title: 二进制编辑器（C++）
ms.date: 02/14/2019
f1_keywords:
- vc.editors.binary.F1
- vc.editors.binary
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
- binary data, editing
- resources [C++], opening for binary editing
- binary data
- hexadecimal bytes in binary data
- strings [C++], searching for
- file searches [C++]
- binary data, finding
- ASCII characters, finding in binary data
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 591a6714f1adabb30fda446cad0e79e2c28c30ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215236"
---
# <a name="binary-editor-c"></a>二进制编辑器（C++）

> [!CAUTION]
> 在**二进制编辑器**中编辑对话框、图像或菜单等资源是很危险的。 不正确的编辑可能会损坏资源，导致其在其本机编辑器中无法读取。

**二进制编辑器**允许在二进制级别编辑十六进制或 ASCII 格式的任何资源。 还可以使用 [查找命令](/visualstudio/ide/reference/find-command) 来搜索 ASCII 字符串或十六进制字节。 仅当需要查看或更改 Visual Studio 环境不支持的自定义资源或资源类型时，才应使用**二进制编辑器**。 **二进制编辑器**在 Express 版本中不可用。

- 若要在新文件上打开**二进制编辑器**，请前往菜单**文件** > **新建** > **文件**，选择要编辑的文件的类型，然后选择 "**打开**" 按钮旁边的下拉箭头，然后选择 "使用 > **二进制编辑器** **打开**"。

- 若要在现有文件上打开**二进制编辑器**，请前往菜单**文件** > **打开** > **文件**"，选择要编辑的文件，然后选择"**打开**"按钮旁边的下拉箭头，然后选择"**使用** > **二进制编辑器**打开 "。

   ![二进制编辑器](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   **二进制编辑器**中显示的对话框的二进制数据

**二进制编辑器**中仅显示某些 ASCII 值（0X20 到0x7E）。 扩展字符在**二进制编辑器**的 "右面板 ASCII 值" 部分中显示为句点。 可打印字符是 ASCII 值32到126。

> [!TIP]
> 使用**二进制编辑器**时，在许多情况下，您可以右键单击以显示特定于资源的命令的快捷菜单。 可用命令取决于所指向的光标。 例如，如果在指向**二进制编辑器**时选择了十六进制值，则右键单击时，快捷菜单会显示**剪切**、**复制**和**粘贴**命令。

## <a name="how-to"></a>如何

利用**二进制编辑器**，您可以：

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>打开 Windows 桌面资源进行二进制编辑

1. 在 [资源视图](how-to-create-a-resource-script-file.md#create-resources)中，选择要编辑的特定资源文件。

1. 右键单击该资源，然后选择 "**打开二进制数据**"。

> [!NOTE]
> 如果使用 "**资源视图**" 窗口打开 Visual Studio 无法识别其格式的资源（如 RCDATA 或自定义资源），则该资源会自动在**二进制编辑器**中打开。

### <a name="to-open-a-managed-resource-for-binary-editing"></a>打开托管资源进行二进制编辑

1. 在**解决方案资源管理器**中，选择要编辑的特定资源文件。

1. 右键单击该资源，然后选择 "**打开方式**"。

1. 在“打开方式” 对话框中，选择“二进制编辑器”。

> [!NOTE]
> 您可以使用[图像编辑器](../windows/image-editor-for-icons.md)和**二进制编辑器**处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。

### <a name="to-edit-a-resource"></a>编辑资源的步骤

如果要对已在另一个编辑器窗口中进行编辑的资源使用**二进制编辑器**，请先关闭其他编辑器窗口。

1. 选择要编辑的字节。

   **Tab**键在**二进制编辑器**的十六进制和 ASCII 部分之间移动焦点。 您可以使用**Page Up**和**page Down**键在资源中一次移动一屏。

1. 键入新值。

   值立即在十六进制和 ASCII 部分中更改，并将焦点移到下一行中的下一个值。

> [!NOTE]
> 关闭编辑器时，**二进制编辑器**会自动接受更改。

### <a name="to-find-binary-data"></a>查找二进制数据

可以搜索 ASCII 字符串或十六进制字节。 例如，若要查找*Hello*，可以搜索字符串 " *hello* " 或其十六进制值 " *48 65 6C 6C 6F*"。

1. 中转到菜单**编辑** > [查找](/visualstudio/ide/reference/find-command)。

1. 在 "**查找内容**" 框中，从下拉列表中选择之前的搜索字符串或键入要查找的数据。

1. 选择任一 "**查找**" 选项，然后选择 "**查找下一个**"。

### <a name="to-create-a-new-custom-or-data-resource"></a>创建新的自定义资源或数据资源

您可以创建新的自定义资源或数据资源，只需要使用常规资源脚本（.rc）文件语法将资源置于单独的文件中，然后在**解决方案资源管理器**中右键单击项目并选择 "**资源包括**" 即可包含该文件。

1. [创建 .rc 文件](../windows/how-to-create-a-resource-script-file.md) （其中包含自定义资源或数据资源）。

   可以在 .rc 文件中键入自定义数据，格式为以 null 结尾的带引号的字符串，或十进制、十六进制或八进制格式的整数。

1. 在**解决方案资源管理器**中，右键单击项目的 .rc 文件，然后选择 "**资源包括**"。

1. 在 "**编译时指令**" 框中，键入一个 `#include` 语句，该语句提供包含自定义资源的文件的名称，例如：

    ```cpp
    #include mydata.rc
    ```

   请确保所键入内容的语法和拼写正确。 将**编译时指令**框的内容插入到资源脚本文件中的内容与键入的内容完全相同。

1. 选择 **"确定"** 以记录所做的更改。

创建自定义资源的另一种方法是将外部文件导入为自定义资源，请参阅[如何：管理资源](../windows/how-to-import-and-export-resources.md)。

> [!NOTE]
> 创建新的自定义资源或数据资源需要 Win32。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>另请参阅

[资源编辑器](../windows/resource-editors.md)
