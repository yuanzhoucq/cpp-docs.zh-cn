---
title: 对话框 （c + +） 控件和代码之间切换 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ef2bcd7dc6bf70f4d0486334d71bd5f7798c83f
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314386"
---
# <a name="switching-between-dialog-box-c-controls-and-code"></a>对话框 （c + +） 控件和代码之间切换

在 MFC 应用程序，你可以双击对话框控件跳转到其处理程序代码或快速创建存根 （stub） 的处理程序函数。

选择控件后，单击**控件事件**按钮或**消息**按钮[属性窗口](/visualstudio/ide/reference/properties-window)若要查看 Windows 消息和事件的完整列表可用于所选的项。 选择要创建或编辑处理程序函数的列表。

### <a name="to-jump-to-code-from-the-dialog-editor"></a>若要从对话框编辑器跳转到代码

1. 双击对话框中要跳转到其最近实现消息处理函数的声明内的控件。 （对于基于 ATL 的对话框类，您总是跳转到构造函数定义。）

### <a name="to-view-events-for-a-control"></a>若要查看控件的事件

1. 选择控件后，单击**控件事件**按钮[属性窗口](/visualstudio/ide/reference/properties-window)。

   > [!NOTE]
   > 单击**控件事件**按钮时*对话框的*在对话框中，你可以展开它以编辑单个控件的事件具有焦点公开所有控件的列表。

   单个控件有焦点在对话框中，您可以右键单击它并选择**添加事件处理程序**从快捷菜单。 这使您可以指定要向其添加处理程序的类。 有关详细信息，请参阅[添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)。

### <a name="to-view-messages-for-a-dialog-box"></a>若要查看消息的对话框

1. 使用选择对话框中，单击**消息**按钮[属性窗口](/visualstudio/ide/reference/properties-window)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框编辑器](../windows/dialog-editor.md)