---
title: 指导设置对话框 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLUs (dialog units)
- Dialog editor, snap to guides
- grid spacing
- guides, settings
- dialog units (DLUs)
- layout grid in Dialog Editor
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
ms.assetid: 55381e1c-146a-4fa7-b1b3-b1492817615f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3533d57aa8230feb4d0e6fcb8689e0210c61bbd8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595499"
---
# <a name="guide-settings-dialog-box"></a>“参考线设置”对话框

## <a name="layout-guides"></a>版式参考线

显示布局参考线设置。

### <a name="none"></a>无

隐藏布局工具。

### <a name="rulers-and-guides"></a>标尺和参考线

启用时，将标尺添加到布局工具中;参考线可放在标尺。 默认指南将边距，可以通过拖动移动。 若要放置参考线标尺中单击。 控件指南时控件的上方或旁边它们移到"管理单元"。 一旦将它们附加到它，控件还用指南中进行移动。 当控件所附加到每一侧的指南和参考线移动时，该控件调整大小。

### <a name="grid"></a>Grid

创建布局网格。 新控件将自动对齐到网格中。

## <a name="grid-spacing"></a>网格间距

对话框框单元 (Dlu) 中显示的网格间距的设置。

### <a name="width-dlus"></a>宽度： Dlu

Dlu 中设置布局网格的宽度。 水平 DLU 是由 4 个划分对话框字体平均宽度。

### <a name="height-dlus"></a>高度： Dlu

Dlu 中设置的布局网格的高度。 垂直 DLU 是平均划分的八个对话框字体的高度。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[修改布局网格](../windows/modifying-the-layout-grid.md)  
[对话框编辑器状态（参考线和网格）](../windows/dialog-editor-states-guides-and-grids.md)