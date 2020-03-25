---
title: 如何：在编译时包含资源（C++）
ms.date: 02/14/2019
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
- vc.editors.resourceincludes
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: e931a0246340e81049df6ed0f8e26a4b91b570c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215185"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>如何：在编译时包含资源（C++）

默认情况下，所有资源都位于一个资源脚本（.rc）文件中，但有很多原因导致将资源置于主 .rc 文件以外的文件中：

- 向资源语句添加注释，该注释将在保存 .rc 文件时不会被删除。

- 包括已开发并经过测试且无需进一步修改的资源。 资源编辑器不能编辑包括的任何文件，但没有 .rc 扩展名。

- 若为，则包含不同项目所使用的资源，或源代码版本控制系统中的资源。 这些资源必须存在于修改将影响所有项目的中心位置。

- 包含自定义格式的资源（如 RCDATA 资源）。 RCDATA 资源具有特殊要求，在这种情况下，不能使用表达式作为 `nameID` 字段的值。

如果你的现有 .rc 文件中包含任何满足这些条件的部分，请将这些部分放在一个或多个单独的 .rc 文件中，并使用 "**资源包括**" 对话框将它们包含在项目中。

## <a name="resource-includes"></a>资源包括

可以在编译时将其他文件中的资源添加到项目中，方法是在 "**资源包括**" 对话框中的 "**编译时指令**" 框中列出这些资源。 使用 "**资源包括**" 对话框可以修改项目环境在项目 .rc 文件中存储所有资源的正常工作方式，以及 `Resource.h`中的所有[符号](../windows/symbols-resource-identifiers.md)。

若要开始操作，请打开 "**资源包括**" 对话框，方法是右键单击 "[资源视图](how-to-create-a-resource-script-file.md#create-resources)中的 .rc 文件，选择"**资源包括**"，并注意以下属性：

| properties | 说明 |
|---|---|
| **符号头文件** | 允许你更改存储资源文件的符号定义的标头文件的名称。<br/><br/>有关详细信息，请参阅[更改符号头文件的名称](../windows/changing-the-names-of-symbol-header-files.md)。 |
| **只读符号指令** | 使您能够包含包含不应修改的符号的头文件。<br/><br/>例如，要与其他项目共享的符号文件。 这还可以包括 MFC .h 文件。 有关详细信息，请参阅[包含共享（只读）或计算符号](../windows/including-shared-read-only-or-calculated-symbols.md)。 |
| **编译时指令** | 允许包含独立于主资源文件中的资源创建和编辑的资源文件、包含编译时指令（如有条件地包含资源的指令）或包含自定义格式的资源。<br/><br/>还可以使用 "**编译时指令" 框**来包含标准 MFC 资源文件。 |

> [!NOTE]
> 这些文本框中的条目将分别显示在 `TEXTINCLUDE 1`、`TEXTINCLUDE 2`和 `TEXTINCLUDE 3` 标记的 .rc 文件中。 有关详细信息，请参阅[TN035：通过视觉对象C++使用多个资源文件和头文件](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。

使用 "**资源包括**" 对话框对资源文件进行更改后，必须关闭并重新打开 *.rc*文件才能使更改生效。

### <a name="to-include-resources-in-your-project-at-compile-time"></a>编译时在项目中包含资源

1. 将资源置于具有唯一文件名的资源脚本文件中。 不要使用*项目名称 .rc*，因为这是用于主资源脚本文件的文件的名称。

1. 右键单击[资源视图](how-to-create-a-resource-script-file.md#create-resources)中的 *.rc*文件，然后选择 "**资源包括**"。

1. 在 "**编译时指令**" 框中，添加[#include](../preprocessor/hash-include-directive-c-cpp.md)编译器指令以将新的资源文件包含在开发环境中的主资源文件中。

以这种方式包含的文件中的资源仅在编译时成为可执行文件的一部分，当你处理项目的主 .rc 文件时，不能对其进行编辑或修改。 包括 .rc 文件需要单独打开，资源编辑器不能编辑任何不带 .rc 扩展名的文件。

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>为特定资源（.rc）文件指定包含目录

1. 右键单击**解决方案资源管理器**中的 *.rc*文件，然后选择 "**属性**"。

1. 选择左窗格中的 "**资源**" 节点，然后在 "**附加包含目录**" 属性中指定任何其他包含目录。

### <a name="to-find-symbols-in-resources"></a>在资源中查找符号

1. 中转到菜单**编辑** > [查找符号](/visualstudio/ide/go-to)。

   > [!TIP]
   > 若要在搜索中使用[正则表达式](/visualstudio/ide/using-regular-expressions-in-visual-studio)，请在 "**编辑**" 菜单中选择 "[在文件中查找](/visualstudio/ide/reference/find-command)"，而不是**查找符号**。 在 "[查找](/visualstudio/ide/finding-and-replacing-text)" 对话框和 "**查找内容**" 框中，选择 "**使用：正则表达式**" 复选框，可以从下拉列表中选择一个常规搜索表达式。 从此列表中选择表达式时，会将其替换为 "**查找内容**" 框中的搜索文本。

1. 在 "**查找内容**" 框中，从下拉列表中选择之前的搜索字符串，或键入要查找的快捷键，例如 `ID_ACCEL1`。

1. 选择任一 "**查找**" 选项，然后选择 "**查找下一个**"。

> [!NOTE]
> 无法搜索字符串、快捷键或二进制资源中的符号。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[如何：创建资源](../windows/how-to-create-a-resource-script-file.md)<br/>
[如何：管理资源](../windows/how-to-copy-resources.md)<br/>
