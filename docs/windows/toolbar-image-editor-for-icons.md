---
title: 工具栏 （图标的图像编辑器 c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
ms.assetid: a0af4209-6273-4106-a7c1-0edecc9b5755
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9a454d067881a15f6d125430c304f4b5af71b5d1
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314399"
---
# <a name="toolbar-c-image-editor-for-icons"></a>工具栏 （图标的图像编辑器 c + +）

**的图像编辑器**工具栏包含用于绘制、 绘制、 输入文本、 擦除和操作视图的工具。 它还包含选项选择器，可以选择使用每个工具的选项。 例如，你可以选择从各种画笔宽度、 放大因子和行样式。

> [!NOTE]
> 中提供的所有工具**的图像编辑器**工具栏上，还提供从**映像**菜单 (在**工具**命令)。

![图像编辑器工具栏](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")  
“图像编辑器”工具栏

若要使用**的图像编辑器**工具栏和**选项**选择器中，单击该工具或所需选项。

> [!TIP]
> 将鼠标光标悬停工具栏按钮上时，会出现工具提示。 这些提示可以帮助您确定每个按钮的功能。

与**选项**选择器可以指定宽度的行、 画笔笔画，等等。上的图标**选项**选择器按钮更改您选择具体取决于哪种工具。

![绘制&#45;的图像编辑器工具栏上的形状选择器](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")  
图像编辑器工具栏上的选项选择器

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[显示或隐藏工具栏](displaying-or-hiding-the-toolbar-image-editor-for-icons.md)  
[加速键](../windows/accelerator-keys-image-editor-for-icons.md)  
[图标的图像编辑器](../windows/image-editor-for-icons.md)