---
title: 如何：将资源包括在编译时 （c + +）
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
ms.openlocfilehash: 5768347c32b1856da16310f29e7a4257e18b6a93
ms.sourcegitcommit: e540706f4e2675e7f597cfc5b4f8dde648b007bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676456"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>如何：将资源包括在编译时 （c + +）

默认情况下在一个资源脚本 (.rc) 文件中，但是有很多原因，可以将资源置于主.rc 文件之外的文件的位置中的所有资源：

- 若要向保存.rc 文件时将不会删除的资源语句添加注释。

- 若要包括已开发和测试的资源并且无需进一步修改。 包含在内但没有.rc 扩展名的任何文件不会通过资源编辑器可编辑。

- 若要包括的正在使用的不同项目中，或属于源代码版本控制系统的资源。 这些资源必须存在于一个修改会影响所有项目的中心位置。

- 若要包括自定义格式的资源 （如 RCDATA 资源）。 RCDATA 资源有特殊要求，不能将表达式的值用作`nameID`字段。

如果满足下列任一条件的现有.rc 文件中有一些部分，将这些部分放在一个或多个单独的.rc 文件并将其包含在你的项目使用**资源包括**对话框。

## <a name="resource-includes"></a>资源包括

您可以将资源添加从其他文件到你的项目在编译时通过其列在**编译时指令**框中**资源包括**对话框。 使用**资源包括**对话框中，若要修改的所有资源中都存储项目的.rc 文件和所有项目环境正常工作安排[符号](../windows/symbols-resource-identifiers.md)中`Resource.h`。

若要开始，打开**资源包括**通过右键单击.rc 文件中的对话框中[资源视图](../windows/resource-view-window.md)，选择**资源包括**并记下以下属性：

| 属性 | 描述 |
|---|---|
| **符号头文件** | 可以更改符号定义的资源文件的存储位置的标头文件的名称。<br/><br/>有关详细信息，请参阅[更改符号头文件的名称](../windows/changing-the-names-of-symbol-header-files.md)。 |
| **只读符号指令** | 可以包含标头文件包含不应修改的符号。 例如，符号文件，以与其他项目共享。 这还可以包括 mfc.h 文件。<br/><br/>有关详细信息，请参阅[包括共享 （只读） 或计算符号](../windows/including-shared-read-only-or-calculated-symbols.md)。 |
| **编译时指令** | 可以包括创建和编辑单独从主资源文件中的资源的资源文件包含编译时指令 （如有条件地包括资源这些指令），或包含自定义格式中的资源。 此外可以使用**编译时指令框**包括标准 MFC 资源文件。 |

> [!NOTE]
> 由标记.rc 文件中显示这些文本框中的项`TEXTINCLUDE 1`， `TEXTINCLUDE 2`，和`TEXTINCLUDE 3`分别。 有关详细信息，请参阅[TN035:Visual c + + 中使用多个资源文件和头文件](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。

对资源文件使用进行更改后**资源包括**对话框中，您必须关闭并重新打开.rc 文件的更改才会生效。

### <a name="to-include-resources-in-your-project-at-compile-time"></a>编译时在项目中包含资源

1. 将资源置于具有唯一文件名的资源脚本文件中。 不要使用*projectname*.rc，因为这是用于主资源脚本文件的文件的名称。

1. 右键单击.rc 文件中的[资源视图](../windows/resource-view-window.md)，然后选择**资源包括**从快捷菜单。

1. 在中**编译时指令**框中，添加[#include](../preprocessor/hash-include-directive-c-cpp.md)编译器指令，以在开发环境中在主资源文件中包含新的资源文件。

   包含这样的文件中的资源仅在编译时进行的可执行文件的一部分，并在你的项目的主.rc 文件上时并不可用进行编辑或修改。 需要单独打开包含的.rc 文件，并且包括没有.rc 扩展名的任何文件将无法通过资源编辑器可编辑。

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>若要指定包含对特定资源 （.rc 文件） 的目录

1. 右键单击.rc 文件中的**解决方案资源管理器**，然后选择**属性**。

1. 选择**资源**的左窗格中的节点，并指定任何附加的包含目录**附加包含目录**属性。

### <a name="to-find-symbols-in-resources"></a>在资源中查找符号

1. 转到菜单**编辑** > [查找符号](/visualstudio/ide/go-to)。

   > [!TIP]
   > 若要使用[正则表达式](/visualstudio/ide/using-regular-expressions-in-visual-studio)在搜索中，选择[在文件中查找](/visualstudio/ide/reference/find-command)中**编辑**菜单上，而不是**查找符号**。 选择**使用：正则表达式**中的复选框[查找对话框](/visualstudio/ide/finding-and-replacing-text)然后在**查找内容**框，您可以从下拉列表中选择搜索正则表达式。 当从此列表中选择一个表达式时，它将替换中的搜索文本**查找内容**框。

1. 在中**Find What**框中，从下拉列表中选择以前的搜索字符串或键入想要查找的加速键 (例如， `ID_ACCEL1`)。

1. 选择任一**查找**选项，然后选择**查找下一个**。

> [!NOTE]
> 无法搜索字符串、快捷键或二进制资源中的符号。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[如何：创建资源](../windows/how-to-create-a-resource-script-file.md)<br/>
[如何：管理资源](../windows/how-to-copy-resources.md)<br/>