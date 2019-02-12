---
title: “选择”控件
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
ms.openlocfilehash: a0a21942f6e2c37b96a7a704fadbb9bacc4761c8
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149669"
---
# <a name="selecting-controls"></a>“选择”控件

选择控件以调整大小、 对齐、 移动、 复制，或删除它们，，然后完成所需的操作。 在大多数情况下，您需要选择要使用的大小和对齐方式的工具上的多个控件[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

当控件被选定时，它有带实心 （活动） 在其周围的阴影的边框或空心 （非活动）"大小调整控点，"小方块，显示在选择边框。 当选择多个控件时，主导控件具有坚实的调整大小控点和所有其他所选的控件具有空心调整大小控点。

调整大小或对齐多个控件时**对话框**编辑器使用"主导控件"来确定如何调整大小或对齐其他控件。 默认情况下，主导控件为所选的第一个控件。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-select-multiple-controls"></a>若要选择多个控件

1. 在中[工具箱窗口](/visualstudio/ide/reference/toolbox)，选择**指针**工具。

1. 拖动指针以绘制你想要在对话框中选择的控件周围的选择框。

   当释放鼠标按钮时内, 和相交所选内容框中选择所有控件。

   \- 或 -

   按住**Shift**键并选择你想要在所选内容中包含的控件。

   \- 或 -

   按住**Ctrl**键并选择你想要在所选内容中包含的控件。

## <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>若要从所选控件的组中删除控件或控件添加到所选控件的组

1. 与所选控件的组，按住**Shift**键并选择你想要添加到现有的选定内容或从其中移除的控件。

   > [!NOTE]
   > 按住**Ctrl**键并选择所选内容内的控件将使该控件中所选内容的主要控件。

## <a name="to-specify-the-dominant-control"></a>若要指定主导控件

1. 按住**Ctrl**密钥，然后单击你想要使用影响大小或位置的其他控件的控件*第一个*。

> [!NOTE]
> 主导控件的大小调整句柄是纯色，而下级控件的句柄是空心。 所有进一步调整大小或对齐方式取决于主导控件。

## <a name="to-change-the-dominant-control"></a>若要更改主导控件

1. 清除所有当前所选控件的外部单击当前所选内容。

1. 重复上一过程，首先选择一个不同的控件。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)