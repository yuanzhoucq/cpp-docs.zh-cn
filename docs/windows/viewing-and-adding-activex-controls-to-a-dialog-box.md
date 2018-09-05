---
title: 查看并将 ActiveX 控件添加到对话框中 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.controls.activex
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- Insert ActiveX Control command
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e97393aa6989b7af0a7f3a9a97adaf529f21ba8a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686717"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box"></a>查看 ActiveX 控件并将其添加到对话框

Visual Studio 使你可以将 ActiveX 控件插入对话框中。

### <a name="to-see-the-activex-controls-you-have-available"></a>查看你可使用的 ActiveX 控件

1. 在对话框编辑器中打开一个对话框。

2. 右键单击该对话框主体中的任何位置。

3. 在快捷菜单上，单击“插入 ActiveX 控件” 。

   [“插入 ActiveX 控件”对话框](../windows/insert-activex-control-dialog-box.md) 随即出现，其中显示你系统上的所有 ActiveX 控件。 在该对话框底部，会显示 ActiveX 控件文件的路径。

### <a name="to-add-an-activex-control-to-a-dialog-box"></a>将 ActiveX 控件添加到对话框

1. 在 [“插入 ActiveX 控件”对话框](../windows/insert-activex-control-dialog-box.md)中，选择要添加到对话框中的控件，然后单击“确定” 。

   该控件会出现在对话框中，可以在其中编辑它或为它创建处理程序，就如同处理任何其他控件一样。

   > [!NOTE]
   > 可以将 ActiveX 控件添加到 [工具箱窗口](/visualstudio/ide/reference/toolbox)。

   > [!CAUTION]
   > 分发系统上的每个 ActiveX 控件可能并非都是合法的。 请参阅安装了控件的软件的许可协议，或与软件公司联系。

   可以放置在控件**工具箱**以方便访问的窗口。 有关详细信息，请参阅[工具箱](/visualstudio/ide/reference/toolbox)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)  
[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)  
[ActiveX 控件容器](../mfc/activex-control-containers.md)