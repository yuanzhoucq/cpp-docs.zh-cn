---
title: 如何：创建一个资源脚本文件 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
- vc.resvw.add.MFC
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
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: 9055e0f787c238276d3134c2fa6a8afae0102433
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905675"
---
# <a name="how-to-create-a-resource-script-file-c"></a>如何：创建一个资源脚本文件 （c + +）

> [!NOTE]
> **资源编辑器**在 Express 版本中不可用。
>
> 本材料适用于 Windows 桌面应用程序。 .NET 语言的项目不使用资源脚本文件。 有关详细信息，请参阅[资源文件](../windows/resource-files-visual-studio.md)。

## <a name="to-create-a-new-resource-script-rc-file"></a>创建新资源脚本 (.rc) 文件

1. 将焦点放在你现有的项目文件夹**解决方案资源管理器**，例如， `MyProject`。

   > [!NOTE]
   > 不要将包含解决方案文件夹中的项目文件夹相混淆**解决方案资源管理器**。 如果将焦点放**解决方案**文件夹中中的选项**添加新项**对话框 （在步骤 3) 将不同。

1. 在“项目”菜单上，选择“添加新项”。

1. 在中**添加新项**对话框中，选择**Visual c + +** 文件夹然后选择**资源文件 (.rc)** 右窗格中。

1. 为资源脚本文件中提供一个名称**名称**文本，然后选择**打开**。

现在可以 [创建](../windows/how-to-create-a-resource.md) 新资源并将其添加到你的 .rc 文件中。

> [!NOTE]
> 只能向加载到 Visual Studio IDE 的现有项目添加资源脚本（.rc 文件）。 不能创建独立.rc 文件（项目外的文件）。 可以随时创建[资源模板](../windows/how-to-use-resource-templates.md) （.rct 文件）。

## <a name="to-open-a-resource-script-file-outside-of-a-c-project-standalone"></a>若要打开 c + + 项目 （独立版） 外的资源脚本文件

你可以查看 .rc 文件中的资源，而不必打开项目。 .Rc 文件将在而不是在中打开的文档窗口中打开[资源视图](../windows/resource-view-window.md)窗口 （如它在项目内打开该文件时）。

> [!NOTE]
> 这是一个重要的区别，因为仅当（在项目外部）独立打开该文件时才能显示某些命令。 例如，您可以仅保存文件以不同格式或不同的文件名称在项目外部打开该文件时 (**另存为**命令不可用时在项目内部打开一个文件)。

### <a name="to-open-an-rc-file-outside-a-project"></a>要在项目外部打开 .rc 文件

1. 从**文件**菜单中，选择**打开**，然后选择**文件**。

1. 在中**打开的文件**对话框框中，导航到资源脚本文件，你想要查看，突出显示该文件，然后选择**打开**。

   > [!NOTE]
   > 如果您首次打开项目 (**文件**，**打开**，**项目**)，某些命令将不能给你。 “单独”打开文件意味着不先加载项目而直接打开文件。

### <a name="to-open-multiple-rc-files-outside-a-project"></a>若要在项目外部打开多个 .rc 文件

1. 同时单独打开这两个资源文件。 例如，打开`Source1.rc`和`Source2.rc`。

   1. 从**文件**菜单中，选择**打开**，然后选择**文件**。

   1. 在中**打开文件**对话框框中，导航到想要打开的第一个资源脚本文件 (`Source1.rc`)，突出显示该文件，然后选择**打开**。

   1. 重复上述步骤打开第二个.rc 文件 (`Source2.rc`)。

       .Rc 文件即会在单独的文档窗口中打开。

1. 当同时打开这两个 .rc 文件时，平铺窗口，以便可以同时查看它们：

   - 从**窗口**菜单中，选择**新建水平制表符组**或**新建垂直制表符组**。

       \- 或 -

   - 右键单击其中一个.rc 文件，然后选择**新建水平制表符组**或**新建垂直制表符组**从快捷菜单。

> [!NOTE]
> 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

## <a name="to-open-a-resource-script-file-in-text-format"></a>若要以文本格式打开资源脚本文件

有时可能需要查看项目的资源脚本 (.rc) 文件的内容，而不在特定的资源编辑器中打开资源（如对话框）。 例如，可能需要在资源文件的所有对话框内搜索字符串，而不必分别打开每个对话框。

> [!NOTE]
> 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

以文本格式，以查看其包含的所有资源和完整支持在文本编辑器的全局操作，可以轻松打开资源文件。

> [!NOTE]
> 资源编辑器不直接读取.rc 或`resource.h`文件。 资源编译器将它们编译成由资源编辑器使用的 .aps 文件。 该文件是一个编译步骤，只存储符号数据。 与普通编译过程一样，非符号信息（如注释）在编译过程中将被放弃。 每当 .aps 文件与 .rc 文件不同步时，就会重新生成 .rc 文件（例如，当你进行“保存”时，资源编辑器将覆盖 .rc 文件和 resource.h 文件）。 对资源本身所做的任何更改依然包含在 .rc 文件中，但一旦覆盖 .rc 文件就总会丢失注释。 有关如何保留注释的信息，请参阅[编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。

### <a name="to-open-a-resource-script-file-as-text"></a>以文本格式打开资源脚本文件

1. 从**文件**菜单中，选择**打开**，然后选择**文件**。

1. 在中**打开的文件**对话框框中，导航到你想要以文本格式查看的资源脚本文件。

1. 突出显示该文件，然后在上选择下拉箭头**打开**按钮 （位于按钮的右侧）。

1. 选择**打开**从下拉列表菜单。

1. 在中**打开**对话框中，选择**源代码 （文本） 编辑器**。

1. 从**打开作为**下拉列表中，选择**文本**。

   资源中打开**源代码**编辑器。

\- 或 -

1. 在中**解决方案资源管理器**，右键单击.rc 文件。

1. 从快捷菜单中，选择**打开方式...**，然后选择**源代码 （文本） 编辑器**。

## <a name="to-add-mfc-support-to-resource-script-files"></a>若要向资源脚本文件添加 MFC 支持

通常情况下，生成用于 Windows 使用的 MFC 应用程序[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)，向导将生成一组基本的文件 （包括资源脚本 (.rc) 文件），其中包含 Microsoft 基础的核心功能类 (MFC)。 但是，如果编辑不基于 MFC 的 Windows 应用程序的.rc 文件时，特定于 MFC 框架的以下功能不可用：

- MFC 代码向导

- 菜单提示字符串

- 组合框控件的列表内容

- ActiveX 控件承载

但是，您可以向没有它的现有.rc 文件添加 MFC 支持。

> [!NOTE]
> 这些步骤需要 MFC。

### <a name="to-add-mfc-support-to-rc-files"></a>向 .rc 文件添加 MFC 支持

1. 打开资源脚本文件。

1. 在中[资源视图](../windows/resource-view-window.md)，突出显示资源文件夹 (例如，MFC.rc)。

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，请设置**MFC Mode**属性设置为**True**。

   > [!NOTE]
   > 除了设置此标志之后，.rc 文件还必须是 MFC 项目的一部分。 例如，只需设置**MFC Mode**到**True**在 Win32 中的.rc 文件上项目不会为你提供任何 MFC 功能。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[资源编辑器](../windows/resource-editors.md)