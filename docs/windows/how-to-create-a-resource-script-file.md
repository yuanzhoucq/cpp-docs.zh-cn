---
title: 如何：创建资源（C++）
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
ms.openlocfilehash: c997c7a1b2d7fb3a852a42fa78faf2be6074705e
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444976"
---
# <a name="how-to-create-resources-c"></a>如何：创建资源（C++）

可以通过以下方式为项目创建资源：

- 使用资源脚本文件。

   > [!NOTE]
   > 在添加资源之前，必须执行此步骤。

- 将资源添加到项目并使用**资源视图**。

- 使用资源模板创建自定义资源。

## <a name="use-resource-script-files"></a>使用资源脚本文件

在创建新资源并将其添加到项目之前，必须先创建资源脚本（.rc）文件。

> [!NOTE]
> 只能向加载到 Visual Studio IDE 中的现有项目添加资源脚本文件。 你不能在项目外创建独立资源脚本，尽管可以随时创建资源模板（.rct）文件。

### <a name="to-create-a-resource-script-file"></a>创建资源脚本文件

1. 将焦点放在**解决方案资源管理器**中的现有项目文件夹，例如*MyProject*。

   > [!NOTE]
   > 不要将项目文件夹与**解决方案资源管理器**中的解决方案文件夹混淆。 如果将焦点放在**解决方案**文件夹中，则不会有相同的 "**添加新项**" 选项。

1. 在菜单中，依次指向 "**项目**" > "**添加新项**"。

1. 选择 "**视觉C++对象**" 文件夹，并在右窗格中选择 "**资源文件（.rc）** "。

1. 在 "**名称**" 文本框中为资源脚本文件提供名称，然后选择 "**打开**"。

### <a name="to-open-a-resource-script-file"></a>打开资源脚本文件

您可以在资源脚本文件中查看资源，而无需打开项目。 脚本文件将在文档窗口中打开，而不是**资源视图**。

> [!NOTE]
> 某些命令仅在文件独立打开时才可用，而无需先加载项目即可。 例如，若要使用 "**另存为**" 命令并使用不同的格式或文件名保存文件，则该文件必须是独立打开的。

- 若要在项目外打开资源脚本文件，请在菜单中，依次指向 "**文件**" > "**打开**"，然后选择 "**文件**"。 导航到资源脚本文件，突出显示该文件，然后选择 "**打开**"。

    > [!NOTE]
    > 有时，你可能想要查看项目的资源脚本文件的内容，而无需使用资源编辑器打开资源。 例如，可能需要在资源文件的所有对话框内搜索字符串，而不必分别打开每个对话框。 您可以轻松地以文本格式打开资源文件，以查看它包含的所有资源，并完成文本编辑器支持的全局操作。
    >
    > 若要以文本格式打开资源脚本文件，请使用上一步中 "**打开**" 按钮右侧的下拉箭头，然后选择 "**打开方式**"。 选择 "**源代码（文本）编辑器**"，并从 "**打开方式**" 下拉列表中选择 "**文本**"，然后在**源代码**编辑器中打开资源。

- 若要打开多个资源脚本，请对要打开的每个文件（例如*Source1*和*Source2*）执行上述相同步骤。 然后，当这两个 .rc 文件都在单独的文档窗口中打开时，可以使用 "**窗口**" 菜单或右键单击其中一个文件，然后选择 "**新建水平制表符组**" 或 "**新建垂直制表符组**"。 现在可以平铺窗口，以便可以同时查看它们。

> [!TIP]
> 通过在**解决方案资源管理器**中右键单击 .rc 文件，选择 "**打开方式**"，然后选择 "**源代码（文本）编辑器**"，可以打开资源脚本文件。

使用[mfc 应用程序向导](../mfc/reference/mfc-application-wizard.md)生成适用于 Windows 的 Microsoft 基础类（MFC）应用程序时，该向导将生成一组包含 MFC 核心功能的基本文件，包括资源脚本（.rc）文件。 但是，在为不基于 MFC 的 Windows 应用程序编辑 .rc 文件时，这些特定于 MFC 的功能不可用。 这包括代码向导、菜单提示字符串、组合框控件的列表内容以及 ActiveX 控件托管。

- 若要添加 MFC 支持，在资源脚本文件打开的情况下，在**资源视图**中，突出显示 "资源" 文件夹（例如， *MFC*）。 然后在[属性窗口](/visualstudio/ide/reference/properties-window)中，将**MFC 模式**设置为**True**。

  > [!NOTE]
  > 除了设置**Mfc 模式**，.rc 文件还必须是 mfc 项目的一部分。 对于 Win32 项目中的 .rc 文件，仅将**Mfc 模式**设置为**True**不会为你提供 mfc 功能。

## <a name="create-resources"></a>创建资源

可以将资源创建为新的默认资源，即不基于模板的资源，也可以创建为模板之后的资源。

使用 "**资源视图**" 窗口显示项目中包含的资源文件。 展开顶级文件夹（例如， *Project1*）将显示该文件中的资源类型。 展开每个资源类型以显示该类型的单个资源。

> [!TIP]
> 若要打开 "**资源视图**" 窗口，请转到 "菜单"**视图** > **其他窗口** > **资源视图**或按**Ctrl**+**Shift**+**E**。

你还可以使用右键单击 "**资源视图**" 窗口以启动命令的快捷菜单，或双击标题栏停靠和取消停靠窗口。 右键单击控制窗口行为的命令的标题栏。 有关详细信息，请参阅[Windows 管理](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

**资源视图**windows 包括 "**添加资源**" 对话框，其中包含以下用于将资源添加到C++ windows 桌面应用程序项目的属性：

| 属性 | 说明 |
|---|---|
| **资源类型** | 指定要创建的资源类型。<br/><br/>您可以展开光标和对话框资源类别以显示*位于中的其他资源。\Microsoft Visual Studio \<版本\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct*。 如果需要添加 .rct 文件，请将它们放在此处或指定另一个[包含路径](../windows/how-to-specify-include-directories-for-resources.md)。 在树控件中的顶层显示的资源是 Visual Studio 提供的默认资源。 .Rct 文件中的资源将显示在相应类别下的第二个级别。 对于可以添加的 .rct 文件数没有预设的限制。<br/><br/> |
| **新建** | 根据在 "**资源类型**" 框中选择的类型创建资源，然后在相应的编辑器中打开该资源。<br/><br/>例如，如果您创建一个对话框资源，它将在[对话框编辑器](../windows/dialog-editor.md)中打开该资源。 |
| **Import** | 打开 "**导入**" 对话框以导航到要导入到当前项目中的资源。<br/><br/>可以导入位图、图标、光标、HTML 和声音（。WAV）或自定义资源文件。 |
| **自定义** | 打开 "**新建自定义资源**" 对话框以创建自定义资源。<br/><br/>还包括一个**资源类型**属性，该属性提供一个文本框以输入自定义资源类型的名称。 退出C++时，视觉对象会自动将名称改为大写。 自定义资源仅在[二进制编辑器](../windows/binary-editor.md)中进行编辑。 |

创建新资源时，视觉对象C++将为其分配一个唯一名称，例如 `IDD_Dialog1`。 可以通过在关联的资源编辑器或[属性窗口](/visualstudio/ide/reference/properties-window)中编辑资源属性来自定义此资源 ID。

> [!NOTE]
> 不要指定由 Visual Studio 保留的资源名称或 ID。 保留的名称为 `DESIGNINFO`、`HWB`和 `TEXTINCLUDE`，保留的 ID 是 `255`的。

### <a name="to-create-a-resource"></a>创建资源

- 在**资源视图**中，选择 .rc 文件，然后使用 "**编辑** > "**添加资源**"，然后选择要添加到项目中的资源类型。

   > [!TIP]
   > 还可以在**资源视图**中右键单击 .rc 文件，然后从快捷菜单中选择 "**添加资源**"。

- 在**解决方案资源管理器**中，右键单击项目文件夹，选择 "**添加** > **添加资源**"，然后选择要添加到项目中的资源类型。

   > [!NOTE]
   > 如果你的项目中尚无 .rc 文件，此步骤将创建一个。 然后可以重复此步骤将特定资源类型添加到新的 .rc 文件。

- 在[类视图](/visualstudio/ide/viewing-the-structure-of-code)中，右键单击类，选择 "**添加** > **添加资源**"，然后选择要添加到项目中的资源类型。

- 使用菜单**项目** > "**添加资源**"。

## <a name="use-resource-templates"></a>使用资源模板

资源模板是已另存为 .rct 文件的自定义资源。 然后，资源模板作为创建资源的起点。 资源模板在开发其他资源或共享功能的资源组（如标准控件或重复元素）时节省了时间。 例如，如果要在多个对话框中包含一个 "公司徽标" 图标的 "帮助" 按钮，请创建新的对话框模板，并使用 "帮助" 按钮和徽标对其进行自定义。

自定义资源模板后，将所做的更改保存在模板文件夹或包含路径中指定的位置，以便新的资源模板将显示在 "**添加资源**" 对话框中其资源类型下。 你现在可以根据需要使用新的资源模板。

> [!NOTE]
> 资源编辑器将自动提供一个唯一的资源 ID。 您可以根据需要修改[资源属性](../windows/changing-the-properties-of-a-resource.md)。

> [!NOTE]
> 将特定于语言的模板文件放在主模板目录的子目录中。 例如，仅限英语的模板文件 *\\< 资源模板目录\>\ 1033*。
>
> Visual Studio 中的新.rct 文件搜索 *\Program Files\Microsoft Visual Studio\<版本\>\VC\VCResourceTemplates*， *\Program Files\Microsoft Visual Studio \<版本 > \VC\VCResourceTemplates\\< LCID\>*  （例如 1033 为英语的 LCID)，或在任何位置[包括路径](../windows/how-to-specify-include-directories-for-resources.md)。 如果希望将 .rct 文件存储在其他位置，则必须将该位置添加到包含路径中。

### <a name="to-create-and-use-a-resource-template"></a>创建和使用资源模板

1. 在**解决方案资源管理器**中，右键单击项目，然后选择 "**添加** > **添加新项**"。

1. 在 "**模板：** " 窗格中，选择 "**资源模板文件（.rct）** "。

1. 提供新 *.rct*文件的名称和位置，然后选择 "**打开**"。

   新 *.rct*文件会添加到项目中，并显示在 "**资源**" 文件夹下**解决方案资源管理器**中。

1. 双击 *.rct*文件，在文档窗口中将其打开。 若要添加资源，请在文档窗口中右键单击该文件，然后选择 "**添加资源**"。

   你可以自定义添加的资源并保存 *.rct*文件。

1. 在**资源视图**窗格中，右键单击 *.rc*文件，然后选择 "**添加资源**"。

1. 选择资源旁边的加号（ **+** ），展开资源节点并查看可用于该资源的模板。

1. 双击要使用的模板。

   您可以根据需要在其资源编辑器中修改所添加的资源。

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>将现有资源文件转换为模板

在资源脚本文件打开的情况下，在菜单中，依次指向 "**文件**" > "**保存 \<*文件名*> 为**。 指定位置，然后选择 **"确定"** 。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[如何：管理资源](../windows/how-to-copy-resources.md)<br/>
[如何：在编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)<br/>