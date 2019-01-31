---
title: 查看和将 ActiveX 控件添加到对话框 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
ms.openlocfilehash: 139407ec1d4e1bfad6bb06854dc24b86ce7014e8
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293606"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>查看和将 ActiveX 控件添加到对话框 （c + +）

Visual Studio 使你可以将 ActiveX 控件插入对话框中。

**插入 ActiveX 控件**对话框中，您可以使用时将 ActiveX 控件插入到您的对话框[对话框编辑器](../windows/dialog-editor.md)。 此对话框包含以下属性：

|属性|描述|
|---|---|
|**ActiveX 控件**|显示 Active X 控件的列表。 从该对话框中插入控件不会生成一个包装类。 如果您需要一个包装器类，使用[类视图](/visualstudio/ide/viewing-the-structure-of-code)创建一个 (有关详细信息，请参阅[添加类](../ide/adding-a-class-visual-cpp.md))。 如果 Active X 控件不会出现在此对话框，请尝试安装该控件根据供应商的说明。|
|**路径**|显示在其中找到 ActiveX 控件的文件。|

可以放置在控件**工具箱**以方便访问的窗口。 有关详细信息，请参阅[工具箱](/visualstudio/ide/reference/)。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-see-the-activex-controls-you-have-available"></a>查看你可使用的 ActiveX 控件

1. 在对话框编辑器中打开一个对话框。

1. 在对话框中的正文中，右键单击任意位置。

1. 在快捷菜单上，选择**插入 ActiveX 控件**。

   **插入 ActiveX 控件**对话框出现，其中显示你系统上的所有 ActiveX 控件。 在该对话框底部，会显示 ActiveX 控件文件的路径。

## <a name="to-add-an-activex-control-to-a-dialog-box"></a>将 ActiveX 控件添加到对话框

1. 在中**插入 ActiveX 控件**对话框框中，选择你想要添加到对话框并选择的控件**确定**。

   该控件会出现在对话框中，可以在其中编辑它或为它创建处理程序，就如同处理任何其他控件一样。

   > [!NOTE]
   > 可以将 ActiveX 控件添加到 [工具箱窗口](/visualstudio/ide/reference/toolbox)。

   > [!CAUTION]
   > 分发系统上的每个 ActiveX 控件可能并非都是合法的。 请参阅安装了控件的软件的许可协议，或与软件公司联系。

   可以放置在控件**工具箱**以方便访问的窗口。 有关详细信息，请参阅[工具箱](/visualstudio/ide/reference/toolbox)。

## <a name="to-edit-properties-for-an-activex-control"></a>若要编辑的 ActiveX 控件的属性

提供独立供应商的 ActiveX 控件可能都配备有其自己的属性和特征。 ActiveX 控件的属性显示在**属性**窗口。 此外，创建 ActiveX 控件的编写器的任何属性页中显示**属性页**对话框中 (若要查看**属性页**特定的 ActiveX 控件，请单击**属性页**按钮[属性窗口](/visualstudio/ide/reference/properties-window))。

ActiveX 控件，具体取决于为 ActiveX 控件的一部分的属性表的属性页中显示各个选项卡。

> [!NOTE]
> 以下过程适用于使用属性页编辑 ActiveX 控件。 此外可以浏览，并在新编辑 ActiveX 属性**属性**窗口。

1. 选择**ActiveX**控件。

1. 上**视图**菜单中，选择**属性页**并查看属性。

1. 根据需要在属性页中进行更改。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[ActiveX 控件容器](../mfc/activex-control-containers.md)<br/>
[查看 ActiveX 控件并将其添加到对话框](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)<br/>
[“对话框编辑器”选项卡，工具箱](../windows/dialog-editor-tab-toolbox.md)<br/>
[资源文件](../windows/resource-files-visual-studio.md)<br/>
