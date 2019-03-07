---
title: 资源编辑器 （c + +）
ms.date: 02/14/2019
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
ms.openlocfilehash: 461322076e2de4e2cd89c6d39592989aecc75361
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563012"
---
# <a name="resource-editors-c"></a>资源编辑器 （c + +）

资源编辑器是用于创建或修改 Visual Studio 项目中包含的资源的专用的环境。 Visual Studio 资源编辑器共享技术和接口，以帮助你快速、轻松地创建和修改应用程序资源。 资源编辑器，你可以查看和编辑相应的编辑器和预览资源中的资源。

创建或打开某个资源时，将自动打开相应的编辑器。

> [!NOTE]
> 由于托管的项目不使用资源脚本文件，则必须打开你的资源**解决方案资源管理器**。 可以使用[的图像编辑器](../windows/image-editor-for-icons.md)并[二进制编辑器](binary-editor.md)来处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。

|使用...|编辑...|
|----------------|----------------|
|[快捷键编辑器](../windows/accelerator-editor.md)|Visual C++ 项目中的快捷键对应表。|
|[二进制编辑器](binary-editor.md)|二进制数据信息和 Visual C++、Visual Basic 或 Visual C# 项目中的自定义资源。|
|[对话框编辑器](../windows/dialog-editor.md)|Visual C++ 项目中的对话框。|
|[图像编辑器](../windows/image-editor-for-icons.md)|Visual C++、Visual Basic 或 Visual C# 项目中的位图、图标、光标以及其他图像文件。|
|[菜单编辑器](../windows/menu-editor.md)|Visual C++ 项目中的菜单资源。|
|[Ribbon 编辑器](../mfc/ribbon-designer-mfc.md)|MFC 项目中的功能区资源。|
|[字符串编辑器](../windows/string-editor.md)|Visual C++ 项目中的字符串表。|
|[工具栏编辑器](../windows/toolbar-editor.md)|Visual C++ 项目中的工具栏资源。 **工具栏编辑器**属于**图像编辑器**。|
|[版本信息编辑器](../windows/version-information-editor.md)|Visual C++ 项目中的版本信息。|

> [!NOTE]
> 如果你的项目尚未包含.rc 文件，请参阅[如何：创建资源](../windows/how-to-create-a-resource-script-file.md)。

## <a name="view-and-edit-resources"></a>查看和编辑资源

每种资源类型具有特定于该资源类型的资源编辑器。 可以重新排列、 调整大小、 添加控件和功能，或以其他方式修改资源使用相关联的编辑器的方面。 此外可以编辑中的资源[文本格式](../windows/how-to-open-a-resource-script-file-in-text-format.md)并[二进制格式](../windows/opening-a-resource-for-binary-editing.md)。

某些资源类型是单个文件可以导入和使用各种方式;其中包括位图、 图标、 光标、 工具栏和 html 文件。 此类资源具有文件的名称和[资源标识符](../windows/symbols-resource-identifiers.md)。 其他人，例如对话框、 菜单和在 Win32 项目中，字符串表仅作为的一部分存在的资源脚本 (.rc) 文件或资源模板 (.rct) 文件。

资源也可以在项目外部编辑而无需打开该项目，请参阅[如何：创建资源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

> [!NOTE]
> 可以使用修改资源的属性**属性**窗口。

- 若要编辑的资源，属性在[资源视图](/windows/how-to-create-a-resource-script-file#create-resources)，右键单击你想要编辑，并选择的资源**属性**。  然后，在[属性窗口](/visualstudio/ide/reference/properties-window)，更改所需的资源的属性。

- 若要撤消的对资源的属性所做的更改，请确保所需的资源具有焦点**资源视图**，然后选择**撤消**从**编辑**菜单。

### <a name="win32-resources"></a>Win32 资源

您可以访问中的 Win32 资源[资源视图](/windows/how-to-create-a-resource-script-file#create-resources)窗格。

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>若要在资源编辑器中查看 Win32 资源

1. 转到菜单**视图** > **资源视图**。

1. 如果**资源视图**窗口不是最顶层窗口中，选择**资源视图**选项卡以将它放在顶部。

1. 从**资源视图**，展开包含您想要查看的资源的项目的文件夹。 例如，如果你想要查看对话框资源，展开**对话框**文件夹。

1. 例如，双击该资源**IDD_ABOUTBOX**。

   资源将在适当的编辑器中打开。 例如，对于对话框资源，资源将打开内**对话框编辑器**。

#### <a name="to-delete-an-existing-win32-resource"></a>若要删除现有的 Win32 资源

1. 在中**资源视图**，展开资源类型的节点。

1. 右键单击你想要删除选择的资源**删除**。

> [!TIP]
> 当您已在文档窗口中在项目外部打开.rc 文件时，还可以使用此方法。

### <a name="managed-project-resources"></a>托管的项目资源

由于托管的项目不使用资源脚本文件，则必须打开你的资源**解决方案资源管理器**。 使用[的图像编辑器](../windows/image-editor-for-icons.md)并[二进制编辑器](binary-editor.md)来处理托管项目中的资源文件。 你想要编辑的任何托管的资源必须是链接的资源，Visual Studio 资源编辑器不支持编辑嵌入的资源。

- 若要查看在资源编辑器中，托管的资源中**解决方案资源管理器**，双击该资源，例如， *Bitmap1.bmp*，并在适当的编辑器中打开该资源。

- 若要删除现有的托管的资源，在**解决方案资源管理器**，右键单击你想要删除选择的资源**删除**。

## <a name="preview-resources"></a>预览资源

预览对资源进行，可以查看图形资源，而无需打开它们。 预览功能也很有用的可执行文件后已编译，因为这样的资源标识符更改为数字。 这些数字标识符通常不提供足够的信息，因为预览资源可帮助快速识别它们。

以下资源类型提供可视布局预览：位图、 对话框、 图标、 菜单、 光标和工具栏

以下资源不提供 visual 预览版：Accelerator，清单中，字符串表中，版本信息

> [!NOTE]
> 若要预览资源需要 Win32。

### <a name="to-preview-resources"></a>若要预览资源

1. 在中[资源视图](/windows/how-to-create-a-resource-script-file#create-resources)或文档窗口中，选择你的资源，例如， **IDD_ABOUTBOX**。

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，选择**属性页**按钮。

   > [!TIP]
   > 使用快捷方式，请转到菜单**视图** > **属性页**。

   **属性**资源页将打开，显示该资源的预览。 可以使用**向上**并**向下**箭头键可浏览树控件中**资源视图**或文档窗口。 **属性**页将保持打开状态并显示具有焦点并且可预览的任何资源。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[使用资源文件](../windows/working-with-resource-files.md)<br/>
[资源文件](../windows/resource-files-visual-studio.md)<br/>
[资源标识符（符号）](../windows/symbols-resource-identifiers.md)<br/>