---
title: 使用 256 色调色板 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 256-color palette
- colors [C++], icons and cursors
- cursors [C++], color
- color palettes, 256-color
- palettes, 256-color
- icons, color
ms.assetid: 1506ed00-669b-4a21-b1a4-39b6a84a78bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d9a8952ccdf4477f263a2fb960020e7abba19546
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418146"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>使用 256 色调色板（图标的图像编辑器）

若要通过选择绘制从 256 色调色板，您需要选择中的颜色**颜色**中的调色板[颜色窗口](../windows/colors-window-image-editor-for-icons.md)。

### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>若要从大图标的 256 色调色板选择颜色

1. 大图标或光标，选择或创建新的大图标或光标。

2. 从显示中的 256 种颜色中选择颜色**颜色**中的调色板**颜色**窗口。

   选定的颜色将成为中的当前颜色**颜色**中的调色板**颜色**窗口。

   > [!NOTE]
   > 使用 256 色图像的初始调色板匹配返回的调色板`CreateHalftonePalette`Windows API。 适用于 Windows 外壳程序的所有图标应都使用此面板来防止在调色板实现过程的闪烁。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[加速键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[创建 256 色图标或光标](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)<br/>
[图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)