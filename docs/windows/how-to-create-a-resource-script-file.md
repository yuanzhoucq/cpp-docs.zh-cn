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
ms.openlocfilehash: dbb1d1d4b865380abde189ae6a72a1bfc3755840
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320843"
---
# <a name="how-to-create-resources-c"></a>如何：创建资源 （c + +）

**资源视图**窗口将显示在项目中包含的资源文件。 展开顶部文件夹 (例如， *Project1.rc*) 显示中的资源类型文件和展开每个资源类型显示该类型的单个资源。

> [!TIP]
> 若要打开资源视图窗口，请选择**资源视图**上**视图**菜单 (或使用**Ctrl** + **Shift**  +  **E**)。
>
> 此外可以在使用右键单击**资源视图**窗口来启动命令的快捷菜单，或双击以停靠或取消停靠该窗口的标题栏上。 右键单击标题栏提供了可用于控制窗口的行为的其他命令。 有关详细信息，请参阅[Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

**资源视图**windows 包括**添加资源**对话框具有以下属性将资源添加到 c + + Windows 桌面应用程序项目：

|属性|描述|
|--|----|
|**资源类型**|指定你想要创建的资源类型。<br/><br/>你可以展开光标和对话框资源目录以显示其他资源。 这些资源都位于 Visual Studio...\Microsoft\<版本\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct。 如果添加.rct 文件，则将其放在此目录或指定另一个[包括路径](../windows/how-to-specify-include-directories-for-resources.md)。 之后，这些文件中的资源将显示在相应类别下的第二层。 可以添加的.rct 文件数没有预设的限制。<br/><br/>显示在树控件顶层的资源是 Visual Studio 提供的默认资源。|
|**新建**|创建基于中选择的类型的资源**资源类型**框并在适当的编辑器中打开资源。 例如，如果创建对话框资源，它在中打开[对话框编辑器](../windows/dialog-editor.md)。|
|**Import**|此时将打开**导入**对话框中，您可以导航到该资源你想要导入到当前项目。 您可以导入位图、 图标、 光标、 HTML、 声音 (。WAV)，或自定义资源文件。|
|**自定义**|此时将打开**新的自定义资源**对话框中，您可以在其中创建自定义资源。 仅在二进制编辑器中编辑自定义资源。|

**添加资源**对话框包含**新建自定义资源**对话框与要在 c + + 项目中创建新的自定义资源的以下属性：

|属性|描述|
|--|----|
|**资源类型**|提供一个文本框，输入自定义资源类型的名称。 Visual c + + 在退出时自动将大写名称**新的自定义资源**对话框。|

> [!NOTE]
> **资源编辑器**或**资源视图**在 Express 版本中不可用。

## <a name="resource-scripts"></a>资源脚本

创建并将新资源添加到你的项目之前，必须先创建资源脚本 （.rc 文件）。

> [!NOTE]
> 只能向加载到 Visual Studio IDE 的现有项目添加资源脚本（.rc 文件）。 无法创建独立资源脚本 （外部项目）。 可以随时创建资源模板 （.rct 文件）。

### <a name="to-create-a-resource-script"></a>若要创建资源脚本

1. 将焦点放在你现有的项目文件夹**解决方案资源管理器**，例如*MyProject*。

   > [!NOTE]
   > 不要将包含解决方案文件夹中的项目文件夹相混淆**解决方案资源管理器**。 如果将焦点放**解决方案**文件夹中中的选项**添加新项**对话框将会不同。

1. 在“项目”菜单上，选择“添加新项”。

1. 选择**Visual c + +** 文件夹，然后选择**资源文件 (.rc)** 右窗格中。

1. 为资源脚本中提供的名称**名称**文本框中，然后选择**打开**。

### <a name="to-open-a-resource-script"></a>若要打开资源脚本

可以在资源脚本中查看资源，而无需打开一个项目。 脚本文件将在相对于一个文档窗口中打开**资源视图**窗口。

> [!NOTE]
> （在外部项目） 独立打开的文件时，某些命令才可用。 打开文件独立意味着不先加载项目的情况下打开它。
>
> 例如，若要将文件保存在不同的格式或作为不同的文件名称 (作为**另存为**命令是在项目内的文件不可用)。 如果您打开项目先使用**文件** > **打开** > **项目**，这些命令将不可用。

#### <a name="to-open-a-resource-script-outside-of-a-project"></a>若要打开资源脚本在项目外部

1. 从**文件**菜单中，选择**打开**，然后选择**文件**。

1. 导航到资源脚本文件，突出显示该文件，然后选择**打开**。

#### <a name="to-open-multiple-resource-scripts-outside-of-a-project"></a>若要打开在项目外的多个资源脚本

1. 同时单独打开这两个资源文件。 例如，打开*Source1.rc*并*Source2.rc*。

1. 从**文件**菜单中，选择**打开**，然后选择**文件**。

1. 导航到想要打开的第一个资源脚本文件 (*Source1.rc*)，突出显示该文件，然后选择**打开**。

1. 重复上述步骤打开第二个.rc 文件 (*Source2.rc*)。

   这两个.rc 文件即会打开在单独的文档窗口中。

1. 使用**窗口**菜单 （或右键单击一个.rc 文件中的），然后选择**新建水平制表符组**或**新建垂直制表符组**。

   现在平铺窗口，以便可以同时查看它们。

有时可能需要查看项目的资源脚本 (.rc) 文件的内容，而不在特定的资源编辑器中打开资源（如对话框）。 例如，可能需要在资源文件的所有对话框内搜索字符串，而不必分别打开每个对话框。

以文本格式，以查看其包含的所有资源和完整支持在文本编辑器的全局操作，可以轻松打开资源文件。

> [!NOTE]
> 资源编辑器不直接读取.rc 或`resource.h`文件。 资源编译器将它们编译成由资源编辑器使用的 .aps 文件。 该文件是一个编译步骤，只存储符号数据。 与普通编译过程一样，非符号信息（如注释）在编译过程中将被放弃。 每当.aps 文件与.rc 文件获取同步，重新生成.rc 文件 (例如，保存时，资源编辑器将覆盖.rc 文件和`resource.h`文件)。 对资源本身的任何更改依然包含在.rc 文件，但一旦覆盖.rc 文件注释都将丢失。 有关如何保留注释的信息，请参阅[在编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。

### <a name="to-open-a-resource-script-file-in-text-format"></a>若要以文本格式打开资源脚本文件

1. 从**文件**菜单中选择**打开**，然后选择**文件**。

1. 在中**打开的文件**对话框框中，导航到你想要以文本格式查看的资源脚本文件。

1. 突出显示该文件，然后在上选择下拉箭头**打开**（上按钮的右侧） 按钮。

1. 选择**打开**从该下拉列表菜单，然后选择**源代码 （文本） 编辑器**。

1. 从**打开作为**下拉列表中，选择**文本**。

   资源中打开**源代码**编辑器。

> [!TIP]
> 此处的快捷方式是右键单击.rc 文件中的**解决方案资源管理器**，选择**打开方式...** ，然后选择**源代码 （文本） 编辑器**。

## <a name="resources"></a>资源

为新的默认资源 （不基于模板的资源） 或模仿模板的资源，可以创建资源。

当创建新资源时，Visual c + + 的唯一名称为其指定，例如， `IDD_Dialog1`。 可通过在关联的资源编辑器中或 [“属性窗口”](/visualstudio/ide/reference/properties-window)中编辑该资源的属性来自定义该资源 ID。

> [!NOTE]
> 未指定资源名称或保留的 Visual Studio 的 ID。 保留的名称为 DESIGNINFO、 HWB 和 TEXTINCLUDE，保留的 ID 为 255。

### <a name="to-create-a-resource"></a>若要创建资源

可以创建新的资源使用以下项之一：

- 在中**资源视图**，选择你的.rc 文件，然后使用**编辑** > **添加资源**，然后选择要添加到你的项目资源的类型。

   > [!TIP]
   > 此外可以右键单击.rc 文件中的**资源视图**，然后选择**添加资源**从快捷菜单。

- 在中**解决方案资源管理器**，右键单击项目文件夹，选择**添加** > **添加资源**，然后选择要添加到你的项目资源的类型。

   > [!NOTE]
   > 如果还没有在项目中的.rc 文件，此步骤将创建一个。 然后可以重复此步骤将特定资源类型添加到新的 .rc 文件。

- 在中[类视图](/visualstudio/ide/viewing-the-structure-of-code)，右键单击类，选择**添加** > **添加资源**，然后选择要添加到你的项目资源的类型。

- 在中**项目**菜单中，选择**添加资源**。

### <a name="support-for-mfc"></a>对 MFC 的支持

通常情况下，如果您构建 Windows 使用的 Microsoft 基础类 (MFC) 应用程序[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)，向导将生成一组基本的文件 （包括资源脚本 (.rc) 文件），其中包含的核心功能MFC。 但是，在编辑不基于 MFC 的 Windows 应用程序的.rc 文件时，以下特定于 MFC 的功能不可用：MFC 代码向导，菜单提示字符串，列出的组合框控件和 ActiveX 控件承载的内容。

#### <a name="to-add-mfc-support-to-a-resource-script-file"></a>若要向资源脚本文件添加 MFC 支持

1. 打开资源脚本文件。

1. 在中**资源视图**，突出显示资源文件夹 (例如， *MFC.rc*)。

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，请设置**MFC Mode**属性设置为**True**。

   > [!NOTE]
   > 除了设置此属性，.rc 文件必须是 MFC 项目的一部分。 例如，只需设置**MFC Mode**到**True**在.rc 文件包括在 Win32 项目不会为您的 MFC 功能。

## <a name="resource-templates"></a>资源模板

资源模板是已保存为.rct 文件的自定义的资源。 资源模板然后可作为起点来创建的资源。 资源模板可节省开发其他资源或共享功能，例如标准控件或重复元素的资源组的时间。 例如，如果你想要在几个对话框中包含公司徽标图标的帮助按钮，创建新的对话框模板并在其中自定义帮助按钮和徽标。

自定义资源模板之后, 将所做的更改保存在模板文件夹 （或包含路径中指定的位置），以便新的资源模板将显示中的资源类型下**添加资源**对话框。 根据需要现在可以随时使用新的资源模板。

> [!NOTE]
> 资源编辑器将自动提供一个唯一的资源 ID。 您可以修订[资源属性](../windows/changing-the-properties-of-a-resource.md)根据需要。

> [!NOTE]
> 将特定于语言的模板文件放在主模板目录的子目录中。 例如，将在仅限英语的模板文件...\\< 资源模板目录\>\1033。 Visual Studio 搜索 \Program Files\Microsoft Visual Studio 中的新 RCT 文件\<版本\>\VC\VCResourceTemplates，在 Visual Studio \Program Files\Microsoft\<版本 > \VC\VCResourceTemplates\\< LCID\> （例如 1033 为英语)，*或*上的任何位置[包括路径](../windows/how-to-specify-include-directories-for-resources.md)。 如果想要将 RCT 文件存储在另一个位置，例如我的文档，您需要将此文件夹添加到包含路径，以便 Visual Studio 可以找到该 RCT 文件。

### <a name="to-create-a-resource-template"></a>若要创建的资源模板

1. 在中**解决方案资源管理器**，右键单击你的项目。

1. 从快捷菜单中，选择**外** > **添加新项**。

1. 在中**模板：** 窗格中，选择**资源模板文件 (.rct)**。

1. 提供的名称和新的.rct 文件的位置，并选择**打开**。

   新的.rct 文件添加到你的项目，并显示在**解决方案资源管理器**下**资源**文件夹。

1. 双击.rct 文件以在文档窗口中打开它。 若要添加的资源，请右键单击文档窗口中的文件，然后选择**添加资源**。

   可以自定义这些资源，并保存为.rct 文件。

### <a name="to-create-a-new-resource-from-a-template"></a>若要从模板创建新资源

1. 在中**资源视图**窗格中，右键单击.rc 文件，然后选择**添加资源**从快捷菜单。

1. 选择加号 (**+**) 旁边的展开资源节点并查看所有模板可用于该资源的资源。

1. 双击要使用的模板。

1. 根据需要在相应的资源编辑器中修改已添加的资源。

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>若要将现有的资源文件转换为模板

1. 为独立的文件打开.rc 文件。

1. 上**文件**菜单中，选择**保存\< *filename*> 为**。

1. 指定一个位置，然后选择**确定**。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[管理资源](../windows/how-to-copy-resources.md)<br/>
[在编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)<br/>