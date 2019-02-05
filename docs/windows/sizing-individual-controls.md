---
title: 调整控件的大小
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.combo
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
ms.openlocfilehash: a6381dcf1aeb9f73ac3b656229d9332df2a6a519
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742708"
---
# <a name="sizing-controls"></a>调整控件的大小

使用大小调整句柄来调整控件的大小。 仅当鼠标指针置于调整大小控点时，它将改变形状以指示可以在其中调整控件的说明操作。 活动的调整大小控点都是可靠;如果大小调整句柄是空心，控件不能沿该轴的大小调整。

此外可以通过将控件与参考线或边距，对齐更改控件的大小，或通过将移动一个对齐控件和参考线彼此。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-size-an-individual-control"></a>调整单个控件的大小

1. 选择的控件。

1. 拖动调整大小控点，若要更改控件的大小：

   - 在顶部和边的调整大小控点更改水平或垂直大小。

   - 角的调整大小控点更改水平和垂直大小。

   > [!TIP]
   > 可以通过按下一次调整控件一个对话框单元 （dlu） 地**Shift**密钥和使用**向右箭头**并**向下箭头**密钥。

## <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>若要自动调整大小以适应其中的文本的控件

选择**内容调整大小**从**格式**菜单。

\- 或 -

右键单击该控件，然后选择**内容调整大小**从快捷菜单。

## <a name="to-make-controls-the-same-width-height-or-size"></a>若要使控件相同的宽度、 高度或大小

您可以调整大小一的组基于主导控件大小的控件。

1. [选择的控件](../windows/selecting-multiple-controls.md)要重设大小。

   所选序列中的第一次控件是主导控件。 主导控件的大小取决于组中控件的最终大小。 选择主导控件的详细信息，请参阅[指定主导控件](../windows/specifying-the-dominant-control.md)。

1. 从**格式**菜单中，选择**使大小相同**，然后选择下列命令之一：

   - **两者**

   - **Height**

   - **Width**

## <a name="to-set-the-size-of-the-combo-box-and-its-drop-down-list"></a>若要设置的组合大小框和下拉列表

时将其添加到对话框中，可以调整组合框的大小。 此外可以指定下拉列表框的大小。 有关详细信息，请参阅[添加到组合框控件的值](../windows/adding-values-to-a-combo-box-control.md)。

### <a name="to-size-a-combo-box"></a>若要组合框的大小

1. 在对话框中选择的组合框控件。

   最初，仅左侧和右侧的调整大小控点处于活动状态。

1. 使用大小调整句柄设置组合框的宽度。

此外可以设置组合框的下拉部分的垂直大小。

### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>若要设置的组合大小框下拉列表

1. 选择组合框右侧的下拉箭头按钮。

   ![在 MFC 项目组合框上的箭头](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   此控件改为使用扩展的下拉列表区域显示组合框的大小的轮廓。

1. 使用较低的调整大小控点更改下拉列表区域的初始大小。

   ![组合&#45;MFC 项目中的框大小调整](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. 选择下拉箭头以关闭组合框的下拉列表部分。

## <a name="to-set-the-width-of-a-horizontal-scroll-bar-and-make-it-appear"></a>若要将水平滚动条的宽度设置，使其看起来

当将具有水平滚动条的列表框添加到使用 MFC 类在应用程序中不会自动显示滚动条的对话框。

通过调用设置提供给最大元素的最大宽度[CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent)在代码中。

   如果不设置此值，滚动条不会显示，甚至当列表框中的项都超过框。
> [!NOTE]
> 水平滚动条要求 MFC。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)
