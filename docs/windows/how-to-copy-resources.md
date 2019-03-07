---
title: 如何：管理资源 （c + +）
ms.date: 02/14/2019
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
- vb.xmldesigner.data
- vs.resvw.resource.importing
- vc.resvw.resource.importing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
- .resx files [C++], editing
- resource files [C++], editing
- resx files [C++], editing
- resources [C++], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [C++], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 28127ea89fdba1b70988ced1d6004c0f914c66e2
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563038"
---
# <a name="how-to-manage-resources-c"></a>如何：管理资源 （c + +）

## <a name="copy-and-edit-resources"></a>复制和编辑资源

可以复制资源从一个文件到另一个不更改它们，或将其复制时更改语言或资源的条件。

可以轻松地从现有的资源或可执行文件的资源复制到当前的资源文件。 若要复制的资源，您打开这两个文件同时包含资源和将项从一个文件拖动到另一种或复制并粘贴在两个文件之间。 此方法适用于资源脚本 (.rc) 文件和资源模板 (.rct) 文件，以及作为可执行文件 (.exe) 文件。

> [!NOTE]
> Visual c + + 包括可以在自己的应用程序中使用的示例资源文件。 有关详细信息，请参阅[剪贴画：公共资源](https://github.com/Microsoft/VCSamples)。

您不能拖放、 复制、 剪切、 或在项目中的资源文件之间粘贴 (**资源视图**) 并在文档窗口中打开独立.rc 文件。 无法在以前版本的产品来执行此操作。 仅在项目外部打开.rc 文件之间使用拖放方法。

### <a name="to-copy-resources"></a>若要将资源复制

1. 打开两个独立的资源文件 (请参阅如何[以打开资源脚本文件](/how-to-create-a-resource-script-file#use-resource-script-files))。 例如，打开*Source1.rc*并*Source2.rc*。

1. 在第一个.rc 文件，可以：

   - 使用拖放方法

      1. 选择你想要复制的资源。 例如，在*Source1.rc*，选择**IDD_DIALOG1**。

      1. 按住**Ctrl**密钥，然后将资源拖到第二个.rc 文件。 例如，拖动**IDD_DIALOG1**从*Source1.rc*到*Source2.rc*。

         > [!TIP]
         > 无需按拖动资源**Ctrl**键在移动资源，而不是复制它。

   - 使用复制和粘贴方法

      1. 右键单击该资源与你要复制 (例如， *Source1.rc*)，然后选择**副本**。

      1. 右键单击要在其中粘贴该资源的资源文件 (例如， *Source2.rc*)，然后选择**粘贴**。

> [!NOTE]
> 若要避免使用符号名称或现有文件中的值冲突，Visual c + + 可能会更改传输的资源的符号值或符号名称和值时将其复制到新文件。

在资源中进行复制时，你可以更改其语言属性和/或条件属性。

- 资源的语言指定使用的语言[FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea)以帮助识别要查找的资源。 资源可能存在的每种语言不与文本相关的差异，例如，可能仅适用于日语键盘的加速器或仅将适用于中文本地化的位图生成。

- 资源的条件是定义的符号，后者标识了使用资源的此特定副本的条件。

语言和资源的条件都显示在括号中的中的资源名称后**工作区**窗口。 此处指定的资源`IDD_AboutBox`使用`Finnish`作为其语言和它的条件是`XX33`:

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>复制的现有资源并更改其语言或条件

在中 *.rc*文件中或在[资源视图](../windows/resource-view-window.md)窗口中，右键单击你想要复制，并选择的资源**插入副本**。 然后设置以下各项：

- 有关**语言**列表框中，选择的语言。

- 在中**条件**框中，键入条件。

### <a name="to-edit-resources"></a>若要编辑的资源

托管的资源 (.resx) 文件是 XML 文件。 当将托管的资源文件添加到你的项目从**添加新项**对话框中，**托管资源编辑器**默认情况下打开。

## <a name="import-and-export-resources"></a>导入和导出资源

可以导入图形资源（位图、图标、光标和工具栏）、HTML 文件和自定义资源以便在 Visual C++ 中使用。 可以从 Visual C++ 项目导出相同类型的文件以分隔可以在开发环境外部使用的文件。

> [!NOTE]
> 无法导入或导出，因为它们不是独立的文件类型的资源类型，如加速器、 对话框和字符串表。

### <a name="to-import-a-resource-into-the-resource-script-file"></a>若要将资源导入到资源脚本文件

1. 在中[资源视图](../windows/resource-view-window.md)右键单击你想要将资源添加，然后选择资源脚本 (.rc) 文件的节点**导入**。

1. 找到并选择位图 (.bmp)、 图标 (.ico)、 光标 (.cur)、 html 文件 (.htm) 或要导入其他文件的文件名。

1. 选择**确定**若要将资源添加到资源脚本文件。

> [!NOTE]
> 导入过程的工作方式相同的资源类型的无论所选。 导入的资源自动添加到该资源类型的正确节点。

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>若要导出在 Visual c + + 外部使用的资源

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击你想要导出，然后选择的资源**导出**。 您可以接受当前文件的名称或键入一个新。

1. 导航到要保存该文件并选择的文件夹**导出**。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[如何：创建资源](../windows/how-to-create-a-resource-script-file.md)<br/>
[如何：在编译时添加资源](../windows/how-to-include-resources-at-compile-time.md)<br/>