---
title: 使用颜色 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors, Image editor
- colors [C++]
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97e334e3fa2ea2dc099665876d7df95a367c3b57
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609870"
---
# <a name="working-with-color-image-editor-for-icons"></a>使用颜色（图标的图像编辑器）

**的图像编辑器**包含许多功能，尤其是处理和自定义颜色。 可以设置前景色或背景色、 有限的区域填充颜色，或选择要用作当前前景色或背景颜色的图像上的颜色。 可以在使用工具[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)和中颜色调色板[颜色窗口](../windows/colors-window-image-editor-for-icons.md)创建映像。

所有颜色的单色和 16 色图像所都示**颜色**中的调色板**颜色**窗口。 除了 16 种标准颜色，可以创建您自己的自定义颜色。 调色板中颜色的任何更改将立即更改映像中对应的颜色。

在使用 256 色图标和光标图像**颜色**属性中的[属性窗口](/visualstudio/ide/reference/properties-window)使用。 有关详细信息，请参阅[创建 256 色图标或光标](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)。

> [!NOTE]
> 使用**的图像编辑器**，可以查看 32 位映像，但不能编辑这些。

也可以创建真彩色图像。 但是，真彩色示例不显示在完整调色板**颜色**窗口中; 它们仅在前景色或背景颜色指示符区域中显示。 使用创建真彩色[自定义颜色选择器对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。 有关详细信息，请参阅[自定义或更改颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。

可以将自定义的调色板保存在磁盘上，并根据需要重新加载它们。 最近使用的颜色调色板是保存在注册表中，并自动加载下一次启动 Visual Studio。

- [选择前景色或背景色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)

- [填充用一种颜色的图像的封闭的区域](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)

- [从映像用于其他地方选取颜色](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)

- [选择透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)

- [反转所选内容中的颜色](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)

- [自定义或更改颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)

- [保存和加载不同的颜色调色板](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)

- [颜色窗口](../windows/colors-window-image-editor-for-icons.md)

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[加速键](../windows/accelerator-keys-image-editor-for-icons.md)  