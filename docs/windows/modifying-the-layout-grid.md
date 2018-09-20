---
title: 修改布局网格 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
ms.assetid: ec31f595-7542-485b-806f-efbaeccc1b3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d583bbbfeb4cd426684d1091a165335f7cbb6e64
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441391"
---
# <a name="modifying-the-layout-grid"></a>修改布局网格

当您放置或排列控件在对话框中的时，可用于更精确地定位布局网格。 打开网格时，将显示控件与"对齐"网格的虚线像磁化。 您可以打开和关闭此"对齐网格"功能和更改布局网格单元格的大小。

### <a name="to-turn-the-layout-grid-on-or-off"></a>若要打开或关闭的布局网格

1. 从**格式**菜单中，选择**参考线设置**。

2. 在中[指南设置对话框](../windows/guide-settings-dialog-box.md)，选中或清除**网格**按钮。

   你仍然可以控制在单个网格**对话框中**使用的编辑器窗口**切换网格**按钮[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

### <a name="to-change-the-size-of-the-layout-grid"></a>若要更改布局网格的大小

1. 从**格式**菜单中，选择**参考线设置**。

2. 在中[指南设置对话框](../windows/guide-settings-dialog-box.md)，网格中的单元格 Dlu 中键入的高度和宽度。 最小高度或宽度为 4 个 Dlu。 Dlu 的详细信息，请参阅[对话框上的控件排列](../windows/arrangement-of-controls-on-dialog-boxes.md)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框编辑器状态（参考线和网格）](../windows/dialog-editor-states-guides-and-grids.md)<br/>
[对话框中的控件](../windows/controls-in-dialog-boxes.md)