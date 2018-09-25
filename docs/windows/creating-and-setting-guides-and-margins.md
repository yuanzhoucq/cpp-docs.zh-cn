---
title: 创建和设置参考线和边距 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- guides, clearing
- guides
- Dialog Editor [C++], guides and margins
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
ms.assetid: fafa4545-8f00-436f-b590-300e76601156
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0083affb850f35941ca18709785c9bd5e4fc35e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378249"
---
# <a name="creating-and-setting-guides-and-margins"></a>创建和设置参考线和边距

是否移动控件，添加控件，或重新排列当前布局，指南可帮助您将准确地在对话框中的控件对齐。 参考线显示为蓝色点线横跨编辑器，然后标尺中的相应箭头显示的对话框 (在顶部和左侧和右侧的沿**对话框**编辑器)。

当创建一个对话框时，将提供四个边距。 边距是修改后的参考线，以蓝色点线显示。

### <a name="to-create-a-guide"></a>若要创建参考线

1. 标尺，请在单击一次以创建参考线。 (单击一次创建一个新指南; 双击启动[指南设置对话框](../windows/guide-settings-dialog-box.md)可以在其中指定参考线设置。)

### <a name="to-set-a-guide"></a>若要设置参考线

1. 在对话框中，单击该指南并将其拖动到新位置。 （您可以单击标尺拖动相关联的指南中的箭头）。

   本指南的坐标被显示在窗口底部的状态栏和标尺中。 将指针移动标尺以显示该指南的准确位置中的箭头。

### <a name="to-delete-a-guide"></a>删除参考线

1. 将指南拖出对话框的。

\- 或 -

- 将拖离标尺相应的箭头。

### <a name="to-move-margins"></a>若要移动边距

1. 拖动到新位置的边距。

   若要使边距消失，移动到零位置的边距。 若要使返回的边距，请将鼠标指针放在边距的零位置并将边距移至相应位置。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框编辑器状态（参考线和网格）](../windows/dialog-editor-states-guides-and-grids.md)<br/>
[对话框中的控件](../windows/controls-in-dialog-boxes.md)