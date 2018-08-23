---
title: 在对话框中的控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls, about dialog box controls
- dialog box controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70e3bcfb644893f1dc8b41b9c11a3aee5c92103d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591953"
---
# <a name="controls-in-dialog-boxes"></a>对话框中的控件

可以将控件添加到对话框框中使用[对话框编辑器选项卡](../windows/dialog-editor-tab-toolbox.md)中[工具箱窗口](/visualstudio/ide/reference/toolbox)，这样您就可以选择所需控件并将其拖到对话框的。 默认情况下，工具箱窗口设置为自动隐藏。 它为你的解决方案在左边距上的选项卡时显示对话框编辑器处于打开状态。 但是，您可以将固定**工具箱**通过单击位置到窗口**自动隐藏**窗口右上角的按钮。 有关如何控制此窗口的行为的详细信息，请参阅[窗口管理](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

若要将控件添加到对话框、 重新定位现有控件，或将控件从一个对话框中移动到另一个的最快方法是使用拖放方法。 直到放入对话框的点线中概述了控件的位置。 当您在使用拖放方法向对话框添加控件时，该控件提供适合于该类型的控件的标准高度。

当向对话框添加控件或重新定位时，其最终位置可能由参考线或边距，还是您拥有开启的布局网格。

向对话框添加控件后，可以更改属性，例如其标题[属性窗口](/visualstudio/ide/reference/properties-window)。 可以选择多个控件，并一次性更改它们的属性。

- [添加、编辑或删除控件](adding-editing-or-deleting-controls.md)

- [“选择”控件](../windows/selecting-controls.md)

- [调整单个控件的大小](../windows/sizing-individual-controls.md)

- [使控件具有相同的宽度、高度或大小](../windows/making-controls-the-same-width-height-or-size.md)

- [设置组合框及其下拉列表的大小](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)

- [向组合框控件添加值](../windows/adding-values-to-a-combo-box-control.md)

- [设置水平滚动条的宽度](../windows/setting-the-width-of-a-horizontal-scroll-bar.md)

- [对话框上的控件排列](../windows/arrangement-of-controls-on-dialog-boxes.md)

- [对话框编辑器中的自定义控件](custom-controls-in-the-dialog-editor.md)

- [定义助记键（访问键）](../windows/defining-mnemonics-access-keys.md)

- [指定对话框的位置和大小](../windows/specifying-the-location-and-size-of-a-dialog-box.md)

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[添加对话框控件的事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)  
[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)  
[对话框编辑器](../windows/dialog-editor.md)