---
title: 创建、 移动和编辑工具栏按钮 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: d0f0c6c6-9d7e-42b5-a86a-7558127386e7
ms.openlocfilehash: 2a67123e444ad208eaae74a24b72288f2dbb3bdb
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742695"
---
# <a name="creating-moving-and-editing-toolbar-buttons-c"></a>创建、 移动和编辑工具栏按钮 （c + +）

您可以轻松地创建、 移动、 复制和编辑工具栏按钮。

默认情况下，新的或空白按钮显示工具栏的右侧。 您可以在编辑前移动此按钮。 当创建一个新按钮时，另一个空白按钮将出现编辑按钮右侧。 当您保存一个工具栏时，不会保存空白的按钮。

工具栏按钮的属性包括：

|属性|描述|
|--------------|-----------------|
|**ID**|定义按钮的 ID。 下拉列表提供了常见**ID**名称。|
|**Width**|设置按钮的宽度。 建议使用 16 个像素。|
|**Height**|设置按钮的高度。 一个按钮的高度更改工具栏上的所有按钮的高度。 建议将 15 个像素。|
|**提示**|定义在状态栏中显示的消息。 添加 \n 和名称将工具提示添加到该工具栏按钮。 有关详细信息，请参阅[创建工具提示](../windows/creating-a-tool-tip-for-a-toolbar-button.md)。|

**宽度**并**高度**应用于所有按钮。 用于创建工具栏位图有 2048年的最大宽度。 因此如果将按钮宽度设置为 512，只能有四个按钮，如果将宽度设置为 513，只能有三个按钮。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

请参阅以下操作：

## <a name="to-create-a-new-toolbar-button"></a>若要创建新的工具栏按钮

1. 在中[资源视图](../windows/resource-view-window.md)展开资源文件夹 (例如， *Project1.rc*)。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 展开**工具栏**文件夹，然后选择要编辑的工具栏。

1. 将 ID 分配给工具栏右侧的空白按钮。 您可以通过编辑来实现**ID**属性中的[属性窗口](/visualstudio/ide/reference/properties-window)。 例如，你可能想要提供的工具栏按钮和菜单选项相同的 ID。 在这种情况下，使用下拉列表框选择**ID**的菜单选项。

   或

   选择工具栏右侧的空白按钮 (在**工具栏视图**窗格) 并开始绘制。 分配一个默认按钮命令 ID (ID_BUTTON\<n >)。

您还可以复制并粘贴到为新按钮的工具栏上的图像。

## <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>若要将图像添加到工具栏中，为的按钮

1. 在中[资源视图](../windows/resource-view-window.md)，通过双击它打开工具栏。

1. 接下来，打开你想要添加到您的工具栏图像。

   > [!NOTE]
   > 如果您在 Visual Studio 中打开该映像，将在中打开**图像**编辑器。 此外可以在其他图形程序中打开的图像。

1. 从**编辑**菜单中，选择**副本**。

1. 选择其选项卡顶部的源窗口中切换到您的工具栏。

1. 从**编辑**菜单中，选择**粘贴**。

   图像将显示在工具栏上，为新按钮。

## <a name="to-move-a-toolbar-button"></a>移动工具栏按钮

在中**工具栏视图**窗格中，将你想要将移动到其新位置上工具栏按钮。

## <a name="to-copy-buttons-from-a-toolbar"></a>若要从工具栏中复制按钮

1. 按住**Ctrl**密钥。

1. 在中**工具栏视图**窗格中，将按钮拖到其新位置的工具栏上或某个位置上另一个工具栏。

## <a name="to-delete-a-toolbar-button"></a>若要删除的工具栏按钮

选择工具栏按钮，然后将其拖出工具栏。

## <a name="to-insert-or-remove-space-between-buttons-on-a-toolbar"></a>若要插入或删除上一个工具栏按钮之间的空间

一般情况下，若要插入按钮之间有空格，它们将彼此拖开工具栏上。 若要删除空间，请将它们拖向彼此。

### <a name="to-insert-a-space-before-a-button-that-isnt-followed-by-a-space"></a>若要不后跟一个空格的按钮前插入空格

将按钮拖动到右或向下直到与下一步按钮重叠大约一半。

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-to-keep-the-trailing-space"></a>要插入的按钮后跟一个空格前的空间并且要保留尾随空格

拖动按钮，直到右侧或底部边缘刚好接触下一步按钮，或只是重叠。

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-close-up-that-following-space"></a>若要前插入空格跟一个空格的按钮并关闭该以下空间

将按钮拖动到右或向下直到与下一步按钮重叠大约一半。

### <a name="to-remove-a-space-between-buttons-on-a-toolbar"></a>若要删除在工具栏按钮之间留一个空格

一侧的空间的空间向另一侧上的按钮拖动按钮，直到它与重叠大约一半的下一步按钮。

   如果离开，所拖动的按钮的一侧没有空间并拖动按钮与相邻的按钮，多个中间**工具栏**编辑器还将插入您的按钮在相反一侧的空间拖动。

## <a name="to-change-the-properties-of-a-toolbar-button"></a>若要更改工具栏按钮的属性

1. 在 c + + 项目中，选择工具栏上的按钮。

1. 键入中的新 ID **ID**属性中的[属性窗口](/visualstudio/ide/reference/properties-window)，或使用下拉列表选择一个新**ID**。

## <a name="requirements"></a>要求

MFC 或 ATL

## <a name="see-also"></a>请参阅

[工具栏编辑器](../windows/toolbar-editor.md)
