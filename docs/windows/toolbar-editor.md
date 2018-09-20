---
title: 工具栏编辑器 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0bb329b60b72aae268252ae3ddbcc2c63d4a18f6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389678"
---
# <a name="toolbar-editor-c"></a>工具栏编辑器 （c + +）

**工具栏**编辑器，您可以创建 c + + 工具栏资源并将位图转换为工具栏资源。 **工具栏**编辑器使用的图形化显示来显示工具栏和按钮，非常类似于它们的外观中完成的应用程序。

与**工具栏**编辑器，你可以：

- [创建新工具栏和按钮](../windows/creating-new-toolbars.md)

- [将位图转换为工具栏资源](../windows/converting-bitmaps-to-toolbars.md)

- [创建、移动和编辑工具栏按钮](../windows/creating-moving-and-editing-toolbar-buttons.md)

- [创建工具提示](../windows/creating-a-tool-tip-for-a-toolbar-button.md)

**工具栏**编辑器窗口中显示的按钮图像，图像编辑器窗口相同的两个视图。 拆分栏分隔两个窗格。 你可以将拆分条从一端拖动到另一端来更改窗格的相对大小。 活动窗格将显示选择边框。 主题工具栏位于两个图像视图的上方。

![工具栏编辑器](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")  
工具栏编辑器

**工具栏**编辑器是类似于**映像**编辑器的功能。 菜单项、 图形工具和位图网格是中的那些相同**图像**编辑器。 上没有菜单命令**图像**菜单，以便您可以切换**工具栏**编辑器并**图像**编辑器。 有关使用的详细信息**图形**工具栏中，**颜色**面板中，或**图像**菜单中，请参阅[的图像编辑器](../windows/image-editor-for-icons.md)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

MFC 或 ATL

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
[菜单和其他资源](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)