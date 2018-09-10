---
title: 对齐参考线上的控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2790d9fc3bd4e0af6c86bdbd71be236d8980ab4a
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314984"
---
# <a name="aligning-controls-on-a-guide"></a>在参考线上对齐控件

当移动控件，并参考线对齐控件 （如果不有任何控件之前对齐到指南） 时，控件的大小调整句柄对齐参考线。 一条参考线移动时，会对齐到它的控件也同时移动。 参考指南之一移动时调整大小将与多个指南对齐的控件。

由对话框单元 (Dlu) 定义中确定的指南和控件的间距标尺刻度。 DLU 基于对话框字体，通常的 8 磅 MS Shell Dlg 的大小。 水平 DLU 是由 4 个划分对话框字体平均宽度。 垂直 DLU 是字体的平均除以 8 的高度。

### <a name="to-size-a-group-of-controls-with-guides"></a>若要通过指南大小的一组控件

1. 与参考线对齐控件 （或控件） 的一侧。

2. 拖动控件 （或控件） 的另一端的指南。

   如有必要使用多个控件，大小为每个与第二个参考线对齐。

3. 将移动任一调整大小的控件 （或控件） 的指南。

### <a name="to-change-the-intervals-of-the-tick-marks"></a>若要更改的时间刻度线的间隔

1. 从**格式**菜单中，选择**参考线设置**。

2. 在中[指南设置对话框](../windows/guide-settings-dialog-box.md)，在**网格间距**字段中，指定新的宽度和高度 Dlu。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框编辑器状态（参考线和网格）](../windows/dialog-editor-states-guides-and-grids.md)  
[对话框中的控件](../windows/controls-in-dialog-boxes.md)