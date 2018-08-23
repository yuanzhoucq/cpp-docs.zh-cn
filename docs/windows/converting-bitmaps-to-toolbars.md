---
title: 将位图转换为工具栏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor, converting bitmaps
- toolbars [C++], converting bitmaps
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d5524b1d5ecb3fa4de38f46706f26d2a318fe5ef
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602395"
---
# <a name="converting-bitmaps-to-toolbars"></a>将位图转换为工具栏

可以通过将位图转换来创建新工具栏。 从位图图将转换为工具栏按钮图像。 通常，位图包含在单个位图中，使用每个按钮的一个映像的多个按钮映像。 图像可以是任何大小;默认值为 16 像素宽和图像的高度。 可以指定中的按钮图像的大小[新建工具栏资源对话框](../windows/new-toolbar-resource-dialog-box.md)选择时**工具栏编辑器**从**图像**与图像编辑器中的菜单。

### <a name="to-convert-bitmaps-to-a-toolbar"></a>若要将位图转换为工具栏

1. 打开现有的位图资源中[的图像编辑器](../windows/image-editor-for-icons.md)。 (如果位图不是已在你的.rc 文件中，右键单击.rc 文件中，选择**导入**从快捷菜单中，导航到你想要添加到你的.rc 文件，该位图，然后单击**打开**。)

2. 从**图像**菜单中，选择**工具栏编辑器**。

   [新建工具栏资源对话框](../windows/new-toolbar-resource-dialog-box.md)出现。 您可以更改的宽度和高度与位图匹配的图标图像。 然后显示在工具栏编辑器工具栏图像。

3. 若要完成转换，请更改该命令**ID**的按钮使用[属性窗口](/visualstudio/ide/reference/properties-window)。 键入新**ID**或选择**ID**从下拉列表。

   > [!TIP]
   > **属性**窗口包含一个标题栏中的图钉按钮。 单击此按钮启用或禁用**自动隐藏**窗口。 若要快速循环通过所有工具栏按钮属性而无需重新打开各个属性窗口，关闭**自动隐藏**关闭因此**属性**窗口保持不变。

此外可以通过更改新的工具栏上的按钮的命令 Id[属性窗口](/visualstudio/ide/reference/properties-window)。 编辑新的工具栏上的信息，请参阅[创建、 移动和编辑工具栏按钮](../windows/creating-moving-and-editing-toolbar-buttons.md)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

MFC 或 ATL

## <a name="see-also"></a>请参阅

[创建新工具栏](../windows/creating-new-toolbars.md)  
[工具栏编辑器](../windows/toolbar-editor.md)