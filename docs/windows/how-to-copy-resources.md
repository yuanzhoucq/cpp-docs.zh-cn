---
title: 如何：管理资源（C++）
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
ms.openlocfilehash: 718de310bc4fb0cb0072065bc4e7b7adadb182aa
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890923"
---
# <a name="how-to-manage-resources-c"></a>如何：管理资源（C++）

## <a name="copy-and-edit-resources"></a>复制和编辑资源

你可以在不更改资源的情况下将资源从一个文件复制到另一个文件，或者在复制资源时更改资源的语言或条件。

可以轻松地将资源从现有资源或可执行文件复制到当前资源文件。 若要复制资源，请同时打开包含资源的两个文件，并将项从一个文件拖动到另一个文件，或者在这两个文件之间进行复制和粘贴。 此方法适用于资源脚本（.rc）文件和资源模板（.rct）文件，以及作为可执行文件（.exe）文件。

> [!NOTE]
> 视觉C++对象包括可以在自己的应用程序中使用的示例资源文件。 有关详细信息，请参阅[剪贴画：常见资源](https://github.com/Microsoft/VCSamples)。

不能在项目中的资源文件之间进行拖放、复制、剪切或粘贴（**资源视图**）和文档窗口中打开的独立 .rc 文件。 你可以在以前版本的产品中执行此操作。 仅在项目外部打开的 .rc 文件之间使用拖放方法。

### <a name="to-copy-resources"></a>复制资源

1. 同时单独打开这两个资源文件。 （请参阅[使用资源脚本文件](how-to-create-a-resource-script-file.md#use-resource-script-files)）。 例如，打开 " *Source1* " 和 " *Source2*"。

1. 在第一个 .rc 文件中，可以是：

   - 使用拖放方法

      1. 选择要复制的资源。 例如，在*Source1*中，选择**IDD_DIALOG1**。

      1. 按住**Ctrl**键并将资源拖到第二个 .rc 文件。 例如，将**IDD_DIALOG1**从*Source1*拖到*Source2*。

         > [!TIP]
         > 不按住**Ctrl**键的同时拖动资源会移动资源，而不是复制资源。

   - 使用复制和粘贴方法

      1. 右键单击要复制的资源（例如*Source1*），然后选择 "**复制**"。

      1. 右键单击要将资源粘贴到的资源文件（例如*Source2*），然后选择 "**粘贴**"。

> [!NOTE]
> 若要避免与现有文件中的符号名或值冲突， C++在将已传输资源的符号值或符号名称和值复制到新文件时，视觉对象可能会更改这些值。

在资源中进行复制时，你可以更改其语言属性和/或条件属性。

- 资源的语言指定[system.windows.frameworkelement.findresource](/windows/win32/api/winbase/nf-winbase-findresourcea)使用的语言，以帮助确定要查找的资源。 对于与文本无关的每种语言，资源可能有不同之处，例如，只能在日语键盘或仅适用于中文本地化版本的位图上工作的快捷键。

- 资源的条件是定义的符号，后者标识了使用资源的此特定副本的条件。

资源的语言和条件显示在**工作区**窗口中资源名称后的括号中。 此处名为 `IDD_AboutBox` 的资源使用 `Finnish` 作为其语言，其条件 `XX33`：

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>复制的现有资源并更改其语言或条件

在 *.rc*文件或 "[资源视图](how-to-create-a-resource-script-file.md#create-resources)" 窗口中，右键单击要复制的资源，然后选择 "**插入副本**"。 然后，设置以下各项：

- 对于 "**语言**" 列表框，请选择语言。

- 在 "**条件**" 框中，键入条件。

### <a name="to-edit-resources"></a>编辑资源

托管资源（.resx）文件是 XML 文件。 将托管资源文件从 "**添加新项**" 对话框添加到项目时，默认情况下将打开 "**托管资源编辑器**"。

## <a name="import-and-export-resources"></a>导入和导出资源

可以导入图形资源（位图、图标、光标和工具栏）、HTML 文件和自定义资源以便在 Visual C++ 中使用。 你可以从 Visual Studio C++项目中导出相同类型的文件，以便在开发环境之外使用单独的文件。

> [!NOTE]
> 不能导入或导出资源类型（如加速器、对话框和字符串表），因为它们不是独立的文件类型。

### <a name="to-import-a-resource-into-the-resource-script-file"></a>将资源导入资源脚本文件

1. 在[资源视图](how-to-create-a-resource-script-file.md#create-resources)右键单击要向其添加资源的资源脚本（.rc）文件的节点，然后选择 "**导入**"。

1. 找到并选择位图（.bmp）、图标（.ico）、光标（当前）、html 文件（.htm）或其他要导入的文件的文件名。

1. 选择 **"确定"** 以将资源添加到资源脚本文件中。

> [!NOTE]
> 无论选择哪种资源类型，导入过程都是相同的。 导入的资源会自动添加到该资源类型的正确节点。

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>导出用于视觉对象外的资源C++

1. 在[资源视图](how-to-create-a-resource-script-file.md#create-resources)中，右键单击要导出的资源，然后选择 "**导出**"。 您可以接受当前文件名，也可以键入一个新名称。

1. 导航到要在其中保存该文件的文件夹，然后选择 "**导出**"。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[如何：创建资源](../windows/how-to-create-a-resource-script-file.md)<br/>
[如何：在编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)<br/>