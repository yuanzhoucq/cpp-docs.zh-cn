---
title: 二进制编辑器 （c + +）
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
ms.openlocfilehash: 420c5ecf44f8e8b264d9eafd93de58c0db3bedf4
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210713"
---
# <a name="binary-editor-c"></a>二进制编辑器 （c + +）

> [!CAUTION]
> 编辑资源，例如对话框、 图像或中的菜单**二进制编辑器**是很危险的。 不正确的编辑可能会损坏资源，导致其在其本机编辑器中无法读取。

**二进制编辑器**允许您编辑十六进制或 ASCII 格式的二进制级别的任何资源。 还可以使用 [查找命令](/visualstudio/ide/reference/find-command) 来搜索 ASCII 字符串或十六进制字节。 使用**二进制编辑器**仅当需要进行查看或进行次要更改为自定义资源或资源类型不受 Visual Studio 环境。

若要打开**二进制编辑器**的新文件，请转到菜单**文件** > **新建** > **文件**，选择的类型你想要编辑，然后选择下拉箭头旁的文件**开放**按钮，然后选择**打开** > **二进制编辑器**。

若要打开**二进制编辑器**对现有文件，请转到菜单**文件** > **打开** > **文件**，选择你想要编辑，然后选择下拉箭头旁的文件**开放**按钮，然后选择**打开** > **二进制编辑器**。

   ![二进制编辑器](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   显示在对话框中的二进制数据**二进制编辑器**

只有特定 ASCII 值表示在**二进制编辑器**(0x20 到 0x7E)。 在右侧面板 ASCII 值部分中的扩展的字符显示为句点**二进制编辑器**。 可打印字符是 ASCII 值 32 到 126。

> [!TIP]
> 使用时**二进制编辑器**，在许多情况下你可以右击以显示特定于资源的命令的快捷菜单。 可用命令取决于所指向的光标。 例如，如果单击指向**二进制编辑器**时选择了十六进制值，则快捷菜单会显示**剪切**，**复制**，和**粘贴**命令。

**二进制编辑器**在 Express 版本中不可用。

## <a name="how-to"></a>操作说明

**二进制编辑器**，可以：

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>打开 Windows 桌面资源进行二进制编辑

1. 在 [资源视图](../windows/resource-view-window.md)中，选择要编辑的特定资源文件。

1. 右键单击资源，然后选择**打开二进制数据**。

> [!NOTE]
> 如果您使用[资源视图](../windows/resource-view-window.md)窗口中打开资源的格式的 Visual Studio 无法识别，如 RCDATA 或自定义资源，资源会自动打开在**二进制编辑器**。

### <a name="to-open-a-managed-resource-for-binary-editing"></a>打开托管资源进行二进制编辑

1. 在中**解决方案资源管理器**，选择你想要编辑的特定资源文件。

1. 右键单击资源，然后选择**打开**。

1. 在“打开方式”  对话框中，选择“二进制编辑器” 。

> [!NOTE]
> 可以使用[的图像编辑器](../windows/image-editor-for-icons.md)并**二进制编辑器**来处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。

### <a name="to-edit-a-resource"></a>编辑资源的步骤

> [!NOTE]
> 如果你想要使用**二进制编辑器**上已在另一个编辑器窗口中编辑的资源，先关闭其他编辑器窗口。

1. 选择你想要编辑的字节。

   **选项卡**密钥十六进制和 ASCII 部分之间移动焦点**二进制编辑器**。 可以使用**Page Up**并**Page Down**密钥一次浏览资源的一个屏幕。

1. 键入新值。

   值以十六进制和 ASCII 部分立即更改，并且焦点切换到行中的下一个值。

> [!NOTE]
> **二进制编辑器**关闭编辑器时自动接受更改。

### <a name="to-find-binary-data"></a>若要查找二进制数据

您可以搜索 ASCII 字符串或十六进制字节。 例如，若要查找*Hello*，您可以搜索字符串*Hello*还是十六进制值， *48 65 6C 6 C 6F*。

1. 从**编辑**菜单中，选择[查找](/visualstudio/ide/reference/find-command)。

1. 在中**查找内容**框中，从下拉列表中选择以前的搜索字符串或键入想要查找的数据。

1. 选择任一**查找**选项，然后选择**查找下一个**。

### <a name="to-create-a-new-custom-or-data-resource"></a>创建新的自定义资源或数据资源

可以通过右键单击你的项目中将资源放在单独的文件使用标准资源脚本 (.rc) 文件语法，然后包括该文件创建新的自定义资源或数据资源**解决方案资源管理器**，然后选择**资源包括**。

1. [创建 .rc 文件](../windows/how-to-create-a-resource-script-file.md) （其中包含自定义资源或数据资源）。

   可以在 .rc 文件中键入自定义数据，格式为以 null 结尾的带引号的字符串，或十进制、十六进制或八进制格式的整数。

1. 在中**解决方案资源管理器**，右键单击项目的.rc 文件，然后选择**资源包括**。

1. 在中**编译时指令**框中，键入`#include`语句，为包含自定义资源，例如的文件的名称：

    ```cpp
    #include mydata.rc
    ```

   请确保所键入内容的语法和拼写正确。 内容**编译时指令**框会插入到资源脚本文件，完全按照输入它们。

1. 选择**确定**以记录所做的更改。

若要创建自定义资源的另一种方法是导入自定义资源作为外部文件，请参阅[如何：管理资源](../windows/how-to-import-and-export-resources.md)。

> [!NOTE]
> 创建新的自定义资源或数据资源需要 Win32。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)