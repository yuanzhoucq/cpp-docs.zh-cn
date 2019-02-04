---
title: 使用 256 色调色板（图标的图像编辑器）
ms.date: 11/04/2016
helpviewer_keywords:
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
ms.openlocfilehash: 4e2f2c9ce58799756137bb47db42e52c97a43d39
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702890"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>使用 256 色调色板（图标的图像编辑器）

使用**图像**编辑器、 图标和光标可以是固定大小较大 (64 × 64) 使用 256 色调色板，可供选择。 创建资源后，选择设备映像样式。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-create-a-256-color-icon-or-cursor"></a>若要创建 256 色图标或光标

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**插入资源**从快捷菜单。 (如果已有现有的图像资源在.rc 文件中，例如游标，您可以右键单击**游标**文件夹，然后选择**插入光标**从快捷菜单。)

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 在中[插入资源对话框](../windows/add-resource-dialog-box.md)，选择**图标**或**游标**，然后选择**新建**。

1. 上**图像**菜单中，选择**新设备图像**。

1. 选择所需的 256 色图像样式。

## <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>若要从大图标的 256 色调色板选择颜色

若要通过选择绘制从 256 色调色板，您需要选择中的颜色**颜色**中的调色板[颜色窗口](../windows/colors-window-image-editor-for-icons.md)。

1. 大图标或光标，选择或创建新的大图标或光标。

1. 从显示中的 256 种颜色中选择颜色**颜色**中的调色板**颜色**窗口。

   选定的颜色将成为中的当前颜色**颜色**中的调色板**颜色**窗口。

   > [!NOTE]
   > 使用 256 色图像的初始调色板匹配返回的调色板`CreateHalftonePalette`Windows API。 适用于 Windows 外壳程序的所有图标应都使用此面板来防止在调色板实现过程的闪烁。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[图标和光标：显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
