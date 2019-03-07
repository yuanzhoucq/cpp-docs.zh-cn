---
title: 如何：创建资源 （c + +）
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
- vc.resvw.add.MFC
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
- resource script files [C++], opening in text format
- .rc files [C++], opening in text format
- rc files [C++], opening in text format
- rc files [C++], adding MFC support
- .rc files [C++], adding MFC support
- MFC, adding support to resource scripts files
- resource script files [C++], adding MFC support
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
- language-specific template files [C++]
- resource templates
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: a18c24685ff0d5f65970a094730d1587abffb601
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563025"
---
# <a name="how-to-create-resources-c"></a>如何：创建资源 （c + +）

可以为你的项目来创建资源：

- 使用资源脚本文件。

   > [!NOTE]
   > 在添加资源之前，此步骤是必需的。

- 将资源添加到你的项目，并使用**资源视图**。

- 使用资源模板创建自定义的资源。

## <a name="use-resource-script-files"></a>使用资源脚本文件

创建并将新资源添加到你的项目之前，必须先创建资源脚本 (.rc) 文件。

> [!NOTE]
> 仅可以将资源脚本文件添加到现有项目加载到 Visual Studio IDE。 尽管可以随时创建资源模板 (.rct) 文件，无法创建独立资源脚本在项目外部。

### <a name="to-create-a-resource-script-file"></a>若要创建资源脚本文件

1. 将焦点放在你现有的项目文件夹**解决方案资源管理器**，例如*MyProject*。

   > [!NOTE]
   > 不要将包含解决方案文件夹中的项目文件夹相混淆**解决方案资源管理器**。 如果将焦点放**解决方案**文件夹中，不会有相同**添加新项**选项。

1. 在菜单中，转到**项目** > **添加新项**。

1. 选择**Visual c + +** 文件夹，然后选择**资源文件 (.rc)** 右窗格中。

1. 为资源脚本文件中提供一个名称**名称**文本框中，然后选择**打开**。

### <a name="to-open-a-resource-script-file"></a>若要打开资源脚本文件

可以在资源脚本文件中查看资源，而无需打开一个项目。 脚本文件而不是文档窗口中打开**资源视图**。

> [!NOTE]
> 某些命令才可用的文件是独立打开，这意味着在项目外，而无需先加载项目。 例如，若要使用**另存为**命令和保存具有不同的格式或文件名的文件，该文件必须是独立打开。

- 若要打开的菜单中，在项目外部的资源脚本文件，请转到**文件** > **打开**，然后选择**文件**。 导航到资源脚本文件，突出显示该文件，然后选择**打开**。

    > [!NOTE]
    > 可能存在你想要查看你的项目资源脚本文件的内容，而无需使用资源编辑器打开资源。 例如，可能需要在资源文件的所有对话框内搜索字符串，而不必分别打开每个对话框。 以文本格式，以查看其包含的所有资源和完整支持在文本编辑器的全局操作，可以轻松打开资源文件。
    >
    > 若要以文本格式打开资源脚本文件，请使用下拉箭头，在右侧**打开**按钮在上述步骤中，然后选择**打开**。 选择**源代码 （文本） 编辑器**来回**打开为**下拉列表中，选择**文本**，并在打开该资源**源代码**编辑器。

- 若要打开多个资源脚本，请执行上述相同步骤为你想要打开，例如，每个文件*Source1.rc*并*Source2.rc*。 然后，在单独的文档窗口中打开这两个.rc 文件时，使用**窗口**菜单或右键单击其中一个文件，然后选择**新建水平制表符组**或**新建垂直制表符组**. 现在平铺窗口，以便可以同时查看它们。

> [!TIP]
> 可以通过右键单击.rc 文件中的打开资源脚本文件**解决方案资源管理器**，选择**使用打开**，然后选择**源代码 （文本） 编辑器**。

生成 Windows 使用的 Microsoft 基础类 (MFC) 应用程序时[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)，向导将生成一组基本的文件，包括资源脚本 (.rc) 文件)，其中包含 MFC 的核心功能。 但是，这些特定于 MFC 的功能不可用，编辑不基于 MFC 的 Windows 应用程序的.rc 文件时。 这包括代码向导、 菜单提示字符串、 组合框控件和 ActiveX 控件承载的列表内容。

- 若要在打开的资源脚本文件添加 MFC 支持**资源视图**，突出显示资源文件夹 (例如， *MFC.rc*)。 然后在[属性窗口](/visualstudio/ide/reference/properties-window)，请设置**MFC Mode**到**True**。

  > [!NOTE]
  > 除了设置之外**MFC Mode**，.rc 文件必须是一个 MFC 项目的一部分。 仅设置**MFC Mode**到**True**在.rc 文件包括在 Win32 项目不会为您的 MFC 功能。

## <a name="create-resources"></a>创建资源

为新的默认资源，这意味着不基于模板的资源或模仿模板的资源，可以创建资源。

使用**资源视图**窗口中显示包含在项目中的资源文件。 展开顶部文件夹，例如， *Project1.rc*，该文件中显示的资源类型。 展开每个资源类型显示该类型的单个资源。

> [!TIP]
> 若要打开**资源视图**窗口中，转到菜单**视图** > **资源视图**或按**Ctrl** + **Shift**+**E**。

此外可以在使用右键单击**资源视图**窗口来启动命令的快捷菜单，或双击标题栏，停靠和取消停靠该窗口。 右键单击标题栏的命令的控件窗口的行为。 有关详细信息，请参阅[Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

**资源视图**windows 包括**添加资源**对话框具有以下属性将资源添加到 c + + Windows 桌面应用程序项目：

| 属性 | 描述 |
|---|---|
| **资源类型** | 指定要创建资源的类型。<br/><br/>您可以展开光标和对话框框资源目录以显示更多资源，在位于 *...\Microsoft visual Studio\<版本\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct*。 如果你需要添加.rct 文件，则将其放在此处或指定另一个[包括路径](../windows/how-to-specify-include-directories-for-resources.md)。 显示在树控件中的顶层资源是 Visual Studio 提供的默认资源。 .Rct 文件中的资源显示在相应类别下的第二个级别。 可以添加的.rct 文件数没有预设的限制。<br/><br/> |
| **新建** | 创建基于中选择的类型的资源**资源类型**框并在适当的编辑器中打开该资源。<br/><br/>例如，如果创建对话框资源，它会打开中的资源[对话框编辑器](../windows/dialog-editor.md)。 |
| **Import** | 打开**导入**对话框可以导航到你想要导入到当前项目的资源。<br/><br/>您可以导入位图、 图标、 光标、 HTML、 声音 (。WAV)，或自定义资源文件。 |
| **自定义** | 打开**新的自定义资源**对话框来创建自定义资源。<br/><br/>此外包括**资源类型**提供一个文本框，以便您输入的自定义资源类型名称的属性。 当您退出时，visual c + + 自动将名称变为大写。 自定义资源只能中编辑[二进制编辑器](../windows/binary-editor.md)。 |

当创建新资源时，Visual c + + 的唯一名称为其指定，例如， `IDD_Dialog1`。 可以通过编辑资源属性关联的资源编辑器中或在自定义此资源 ID[属性窗口](/visualstudio/ide/reference/properties-window)。

> [!NOTE]
> 未指定资源名称或保留的 Visual Studio 的 ID。 保留的名称为`DESIGNINFO`， `HWB`，并`TEXTINCLUDE`，，保留的 ID 为`255`。

### <a name="to-create-a-resource"></a>若要创建资源

- 在中**资源视图**，选择你的.rc 文件，然后使用**编辑** > **添加资源**，然后选择要添加到你的项目资源的类型。

   > [!TIP]
   > 此外可以右键单击.rc 文件中的**资源视图**，然后选择**添加资源**从快捷菜单。

- 在中**解决方案资源管理器**，右键单击项目文件夹，选择**添加** > **添加资源**，然后选择要添加到你的项目资源的类型。

   > [!NOTE]
   > 如果还没有在项目中的.rc 文件，此步骤将创建一个。 然后可以重复此步骤将特定资源类型添加到新的 .rc 文件。

- 在中[类视图](/visualstudio/ide/viewing-the-structure-of-code)，右键单击类，选择**添加** > **添加资源**，然后选择要添加到你的项目资源的类型。

- 使用菜单**项目** > **添加资源**。

## <a name="use-resource-templates"></a>使用资源模板

资源模板是已保存为.rct 文件的自定义的资源。 资源模板然后可作为起点来创建的资源。 资源模板可节省开发其他资源或共享功能，例如标准控件或重复元素的资源组的时间。 例如，如果你想要在几个对话框中包含公司徽标图标的帮助按钮，创建新的对话框模板并在其中自定义帮助按钮和徽标。

自定义资源模板之后, 将所做的更改保存在模板文件夹或在 include 路径中，指定的位置，以便新的资源模板将显示中的资源类型下**添加资源**对话框。 根据需要现在可以随时使用新的资源模板。

> [!NOTE]
> 资源编辑器将自动提供一个唯一的资源 ID。 您可以修订[资源属性](../windows/changing-the-properties-of-a-resource.md)根据需要。

> [!NOTE]
> 将特定于语言的模板文件放在主模板目录的子目录中。 例如，仅限英语的模板文件进入 *...\\< 资源模板目录\>\1033*。
>
> Visual Studio 中的新.rct 文件搜索*\Program Files\Microsoft Visual Studio\<版本\>\VC\VCResourceTemplates*， *\Program Files\Microsoft Visual Studio \<版本 > \VC\VCResourceTemplates\\< LCID\>*  （例如 1033 为英语的 LCID)，或在任何位置[包括路径](../windows/how-to-specify-include-directories-for-resources.md)。 如果想要将.rct 文件存储在另一个位置，你必须将位置添加到包含路径。

### <a name="to-create-and-use-a-resource-template"></a>若要创建和使用资源模板

1. 在中**解决方案资源管理器**，右键单击项目并选择**添加** > **添加新项**。

1. 在中**模板：** 窗格中，选择**资源模板文件 (.rct)**。

1. 为新提供的名称和位置 *.rct*文件，然后选择**打开**。

   新 *.rct*文件添加到你的项目，并显示在**解决方案资源管理器**下**资源**文件夹。

1. 双击 *.rct*文件以在文档窗口中打开它。 若要添加的资源，请右键单击文档窗口中的文件，然后选择**添加资源**。

   可以自定义你添加的资源和保存 *.rct*文件。

1. 在中**资源视图**窗格中，右键单击 *.rc*文件，然后选择**添加资源**。

1. 选择加号 (**+**) 旁边的展开资源节点并查看可用于该资源的模板的资源。

1. 双击要使用的模板。

   根据需要在相应的资源编辑器中，可以修改已添加的资源。

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>若要将现有的资源文件转换为模板

在菜单中，打开资源脚本文件，请转到**文件** > **保存\< *filename*> 作为**。 指定一个位置，然后选择**确定**。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[如何：管理资源](../windows/how-to-copy-resources.md)<br/>
[如何：在编译时添加资源](../windows/how-to-include-resources-at-compile-time.md)<br/>