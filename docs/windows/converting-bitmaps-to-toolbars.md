---
title: 将位图转换为工具栏 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.newtoolbarresource
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
ms.openlocfilehash: 31b684ff72e970a6b09748b3925564b0b372d339
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702695"
---
# <a name="converting-bitmaps-to-toolbars-c"></a>将位图转换为工具栏 （c + +）

通过将位图转换，可以在 c + + 项目中创建一个新的工具栏。 从位图图将转换为工具栏按钮图像。 通常，位图包含在单个位图中，使用每个按钮的一个映像的多个按钮映像。 图像可以是任何大小;默认值为 16 像素宽和图像的高度。 可以指定中的按钮图像的大小**新建工具栏资源**对话框中选择时**工具栏编辑器**从**图像**与图像编辑器中的菜单。

**新建工具栏资源**对话框允许您指定的宽度和高度的 c + + 项目中的工具栏资源要添加的按钮。 默认值为 16 × 15 像素。

用于创建工具栏位图有 2048年的最大宽度。 因此，如果您设置**按钮宽度**为 512，只能有四个按钮。 如果将宽度设置为 513，您只能有三个按钮。

该对话框具有以下属性：

|属性|描述|
|---|---|
|**按钮宽度**|提供空间以输入你要从位图资源转换为工具栏资源的工具栏按钮的宽度。 图像裁剪为的宽度和高度指定，和颜色调整为使用标准工具栏颜色 （16 种颜色）。|
|**按钮高度**|提供空间以输入你要从位图资源转换为工具栏资源的工具栏按钮的高度。 图像裁剪为的宽度和高度指定，和颜色调整为使用标准工具栏颜色 （16 种颜色）。|

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-convert-bitmaps-to-a-toolbar"></a>若要将位图转换为工具栏

1. 打开现有的位图资源中[的图像编辑器](../windows/image-editor-for-icons.md)。 (如果位图不是在你的.rc 文件中，右键单击.rc 文件中，选择**导入**从快捷菜单中，导航到你想要添加到你的.rc 文件，该位图，然后选择**打开**。)

1. 从**图像**菜单中，选择**工具栏编辑器**。

   **新建工具栏资源**对话框随即出现。 您可以更改的宽度和高度与位图匹配的图标图像。 然后显示在工具栏编辑器工具栏图像。

1. 若要完成转换，请更改该命令**ID**的按钮使用[属性窗口](/visualstudio/ide/reference/properties-window)。 键入新**ID**或选择**ID**从下拉列表。

   > [!TIP]
   > **属性**窗口包含一个标题栏中的图钉按钮。 选择此按钮启用或禁用**自动隐藏**窗口。 若要快速循环通过所有工具栏按钮属性而无需重新打开各个属性窗口，关闭**自动隐藏**关闭因此**属性**窗口保持不变。

此外可以通过更改新的工具栏上的按钮的命令 Id[属性窗口](/visualstudio/ide/reference/properties-window)。 编辑新的工具栏上的信息，请参阅[创建、 移动和编辑工具栏按钮](../windows/creating-moving-and-editing-toolbar-buttons.md)。

## <a name="requirements"></a>要求

MFC 或 ATL

## <a name="see-also"></a>请参阅

[创建新工具栏](../windows/creating-new-toolbars.md)<br/>
[工具栏编辑器](../windows/toolbar-editor.md)<br/>
[工具栏按钮属性](../windows/toolbar-button-properties.md)<br/>
