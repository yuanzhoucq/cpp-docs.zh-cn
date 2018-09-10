---
title: 将控件添加到对话框 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.dialog
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], adding controls to
ms.assetid: b2a26d19-093f-49ca-93da-fef00dfbb381
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e60c64777ea4b5726721a267bcdd700cd71b4214
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317896"
---
# <a name="adding-a-control-to-a-dialog-box-c"></a>将控件添加到对话框 （c + +）

### <a name="to-add-a-control-to-a-dialog-box"></a>将控件添加到对话框

1. 确保对话框选项卡式窗口是编辑器框架中的当前文档。 如果对话框不是当前文档，则你不会在“工具箱”  中看到“对话框编辑器选项卡” 。

2. 在 [工具箱窗口](../windows/dialog-editor-tab-toolbox.md) 的 [对话框编辑器选项卡](/visualstudio/ide/reference/toolbox)上，选择所需的控件，然后：

   - 单击对话框中想要放置控件的位置。 控件在你单击的位置出现。 有关信息，请参阅 [添加多个控件](../windows/adding-multiple-controls.md)。

       \- 或 -

   - 拖放到该控件从**工具箱**窗口到您的对话框上的位置。 有关详细信息，请参阅 [添加控件时调整其大小](../windows/sizing-a-control-while-you-add-it.md)。

       \- 或 -

   - 双击该控件中的**工具箱**窗口 （显示在对话框中），然后重新定位到所需的位置的控件。

有关上可用的控件的类型信息**工具箱**窗口中，请参阅[对话框编辑器选项卡中，工具箱窗口](../windows/dialog-editor-tab-toolbox.md)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)  
[添加对话框控件的事件处理程序](../windows/adding-event-handlers-for-dialog-box-controls.md)  
[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)