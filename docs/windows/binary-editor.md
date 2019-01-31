---
title: 二进制编辑器 （c + +）
ms.date: 11/04/2016
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
ms.openlocfilehash: 06c4a224b745f5aba8c9105d32489f8ca3109e1c
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293593"
---
# <a name="binary-editor-c"></a>二进制编辑器 （c + +）

> [!WARNING]
> **二进制编辑器**在 Express 版本中不可用。

使用二进制编辑器，可在二进制级别编辑十六进制或 ASCII 格式的所有资源。 还可以使用 [查找命令](/visualstudio/ide/reference/find-command) 来搜索 ASCII 字符串或十六进制字节。 应使用**二进制**编辑器仅当您需要查看或进行次要更改为自定义资源或资源类型不受 Visual Studio 环境。

若要打开**二进制编辑器**，首先选择**文件** > **新建** > **文件**从主菜单中，选择你想要编辑，然后单击下拉箭头旁的文件**开放**按钮，然后选择**打开** > **二进制编辑器**。

> [!CAUTION]
> 编辑对话框、图像或二进制编辑器中的菜单等资源是很危险的。 不正确的编辑可能会损坏资源，导致其在其本机编辑器中无法读取。

> [!TIP]
> 使用时**二进制**编辑器中的，在许多情况下，你可以右击以显示特定于资源的命令的快捷菜单。 可用命令取决于所指向的光标。 例如，如果单击指向**二进制**时选择了十六进制值编辑器中的，快捷菜单会显示**剪切**，**复制**，和**粘贴**命令。

## <a name="binary-editor-how-to"></a>二进制编辑器操作方法

与**二进制**编辑器中，请参阅以下操作：

### <a name="to-open-a-resource-for-binary-editing"></a>若要打开资源进行二进制编辑

#### <a name="to-open-a-windows-desktop-resource"></a>若要打开 Windows 桌面资源

1. 在 [资源视图](../windows/resource-view-window.md)中，选择要编辑的特定资源文件。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 右键单击该资源，然后在快捷菜单中单击“打开二进制数据”  。

   > [!NOTE]
   > 如果您使用[资源视图](../windows/resource-view-window.md)中自动打开窗口，Visual Studio 无法识别 （如 RCDATA 或自定义资源），该资源的格式打开资源**二进制**编辑器。

#### <a name="to-open-a-managed-resource"></a>若要打开托管的资源

1. 在中**解决方案资源管理器**，选择你想要编辑的特定资源文件。

1. 右键单击该资源，然后从快捷菜单选择“打开方式”  。

1. 在“打开方式”  对话框中，选择“二进制编辑器” 。

   > [!NOTE]
   > 可以使用[的图像编辑器](../windows/image-editor-for-icons.md)并[二进制编辑器](binary-editor.md)来处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。

![二进制编辑器](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
二进制编辑器中显示的对话框的二进制数据

只有特定 ASCII 值才会二进制编辑器中进行表示（0x20 到 0x7E）。 扩展字符在二进制编辑器的 ASCII 值部分（右面板）中显示为句点。 “可打印”字符是 ASCII 值 32 到 126。

> [!NOTE]
> 如果你想要使用**二进制**上已在另一个编辑器窗口中，编辑的资源编辑器先关闭其他编辑器窗口。

### <a name="to-edit-a-resource-in-the-binary-editor"></a>若要编辑的二进制编辑器中的资源

1. 选择你想要编辑的字节。

   **选项卡**密钥十六进制和 ASCII 部分之间移动焦点**二进制**编辑器。 可以使用**Page Up**并**Page Down**密钥一次浏览资源的一个屏幕。

1. 键入新值。

   值以十六进制和 ASCII 部分立即更改，并且焦点切换到行中的下一个值。

   > [!NOTE]
   > **二进制**编辑器更改时自动接受关闭编辑器。

### <a name="to-find-binary-data"></a>若要查找二进制数据

您可以搜索 ASCII 字符串或十六进制字节。 例如，若要查找"Hello"，您可以搜索字符串"Hello"或"48 65 6C 6 C 6F"（十六进制等效值）。

1. 从**编辑**菜单中，选择[查找](/visualstudio/ide/reference/find-command)。

1. 在中**查找内容**框中，从下拉列表中选择以前的搜索字符串或键入想要查找的数据。

1. 选择任一**查找**选项。

1. 选择**查找下一个**。

### <a name="to-create-a-new-custom-or-data-resource"></a>创建新的自定义资源或数据资源

可以通过右键单击你的项目中将资源放在单独的文件使用标准资源脚本 (.rc) 文件语法，然后包括该文件创建新的自定义资源或数据资源**解决方案资源管理器**，然后单击**资源包括**快捷菜单上。

1. [创建 .rc 文件](../windows/how-to-create-a-resource-script-file.md) （其中包含自定义资源或数据资源）。

   可以在 .rc 文件中键入自定义数据，格式为以 null 结尾的带引号的字符串，或十进制、十六进制或八进制格式的整数。

1. 在“解决方案资源管理器” 中，右键单击项目的 .rc 文件，然后在快捷方式菜单中单击“资源包含”  。

1. 在中**编译时指令**框中，键入`#include`语句，为包含自定义资源的文件的名称。 例如：

    ```cpp
    #include mydata.rc
    ```

   请确保所键入内容的语法和拼写正确。 在“编译时指令”  框中键入时，其内容会插入到资源脚本文件中。

1. 选择**确定**以记录所做的更改。

创建自定义资源的另一种方法是将外部文件导入为自定义资源。 有关详细信息，请参阅 [导入和导出资源](../windows/how-to-import-and-export-resources.md)。

> [!NOTE]
> 创建新的自定义资源或数据资源需要 Win32。

## <a name="managed-resources"></a>托管资源

可以使用[的图像编辑器](../windows/image-editor-for-icons.md)并**二进制**托管项目的编辑器来处理资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)