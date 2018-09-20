---
title: 将从一种格式图像转换到另一个 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 0409c2bd-3bd8-4d72-9c71-c683b6cf51be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b34b0a55f079962860bb0d9055f19780273d267
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406374"
---
# <a name="converting-an-image-from-one-format-to-another-image-editor-for-icons"></a>将图像从一种格式转换为另一种格式（图标的图像编辑器）

您可以打开 GIF 或 JPEG 图像的方式**图像**编辑器并将其保存为位图。 此外，可以打开一个位图文件，并将其保存为 GIF 或 JPEG。 所处理的图像不需要在开发环境中编辑的项目的一部分 (请参阅[独立图像编辑](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md))。

### <a name="to-convert-an-image-from-one-format-to-another"></a>若要将图像从一种格式转换到另一个

1. 打开中的图像**图像**编辑器。

2. 从**文件**菜单中，选择**保存*filename*作为**。

3. 在**将文件另存为**对话框中**文件名**框中，键入文件名称和扩展名，表示所需的格式。

4. 单击“保存” 。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[图标的图像编辑器](../windows/image-editor-for-icons.md)