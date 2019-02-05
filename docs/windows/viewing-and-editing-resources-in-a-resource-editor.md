---
title: 查看和编辑资源在资源编辑器中 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
ms.openlocfilehash: 02ab58d37f3f188c3d65740b218cb9b2ac799714
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742656"
---
# <a name="viewing-and-editing-resources-in-a-resource-editor-c"></a>查看和编辑资源在资源编辑器中 （c + +）

每种资源类型具有**资源**特定于该资源类型的编辑器。 可以重新排列、 调整大小、 添加控件和功能，或以其他方式修改资源使用相关联的编辑器的方面。 此外可以编辑中的资源[文本格式](../windows/how-to-open-a-resource-script-file-in-text-format.md)并[二进制格式](../windows/opening-a-resource-for-binary-editing.md)。

某些资源类型是单个文件可以导入和使用各种方式;其中包括位图、 图标、 光标、 工具栏和 html 文件。 此类资源具有文件的名称和[资源标识符](../windows/symbols-resource-identifiers.md)。 其他人，例如对话框、 菜单和在 Win32 项目中，字符串表仅作为的一部分存在的资源脚本 (.rc) 文件或资源模板 (.rct) 文件。

> [!NOTE]
> 资源的属性[可以使用属性窗口修改](../windows/changing-the-properties-of-a-resource.md)。

## <a name="win32-resources"></a>Win32 资源

您可以访问中的 Win32 资源[资源视图](../windows/resource-view-window.md)窗格。

### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>若要在资源编辑器中查看 Win32 资源

1. 选择**资源视图**从**视图**菜单。

1. 如果**资源视图**窗口不是最顶层窗口中，选择**资源视图**选项卡以将它放在顶部。

1. 从**资源视图**，展开包含您想要查看的资源的项目的文件夹。 例如，如果你想要查看对话框资源，展开**对话框**文件夹。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 例如，双击该资源**IDD_ABOUTBOX**。

   资源将在适当的编辑器中打开。 例如，对于对话框资源，资源将打开内**对话框**编辑器。

   此外可以[.rc （资源脚本） 文件中查看资源，而无需打开一个项目](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

### <a name="to-delete-an-existing-win-32-resource"></a>若要删除现有 Win 32 资源

1. 在中**资源视图**，展开资源类型的节点。

2. 右键单击你想要删除选择的资源**删除**从快捷菜单。

   > [!NOTE]
   > 可以删除您已在文档窗口中在项目外部打开.rc 文件时使用相同的快捷菜单命令的资源。

## <a name="resources-in-managed-projects"></a>在托管项目中的资源

由于托管的项目不使用资源脚本文件，则必须打开你的资源**解决方案资源管理器**。 可以使用[的图像编辑器](../windows/image-editor-for-icons.md)并[二进制编辑器](binary-editor.md)来处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>若要在资源编辑器中查看托管的资源

在中**解决方案资源管理器**，双击该资源，例如， **Bitmap1.bmp**。

   资源将在适当的编辑器中打开。

### <a name="to-delete-an-existing-managed-resource"></a>若要删除现有的托管的资源

在中**解决方案资源管理器**，右键单击你想要删除选择的资源**删除**从快捷菜单。

## <a name="changing-the-properties-of-resources"></a>更改资源的属性

### <a name="to-edit-the-properties-of-a-resource"></a>编辑资源的属性

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击你想要编辑，并选择的资源**属性**从快捷菜单。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，更改所需的资源的属性。

### <a name="to-undo-a-change-made-to-the-properties-of-a-resource"></a>若要撤消的对资源的属性所做的更改

1. 请确保所需的资源具有焦点**资源视图**。

1. 选择**撤消**从**编辑**菜单。

## <a name="previewing-resources"></a>预览资源

预览对资源进行，可以查看图形资源，而无需打开它们。 预览功能也很有用的可执行文件后，已编译它们，因为资源标识符更改为数字。 这些数字标识符通常不提供足够的信息，因为预览资源可帮助快速识别它们。

您可以预览的可视布局部分的以下资源类型：

- Bitmap

- 对话框

- 图标

- 菜单

- Cursor

- Toolbar

Visual 预览版函数不能应用于加速器、 清单、 字符串表和版本信息资源。

### <a name="to-preview-resources"></a>若要预览资源

1. 在中[资源视图](../windows/resource-view-window.md)或文档窗口中，选择你的资源，例如， **IDD_ABOUTBOX**。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，选择**属性页**按钮。

   \- 或 -

   上**视图**菜单中，选择**属性页**。

   **属性页**资源将打开，显示该资源的预览。 然后，可以使用**向上**并**向下**箭头键可浏览树控件中**资源视图**或文档窗口。 **属性页**将保持打开状态并显示具有焦点并且可预览的任何资源。

> [!NOTE]
> 若要预览资源需要 Win32。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[如何：在项目外打开资源脚本文件（独立）](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
[资源编辑器](../windows/resource-editors.md)