---
title: 对齐控件
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
ms.assetid: a4f49a73-4a17-44b3-8568-aa35f646b5cf
ms.openlocfilehash: abfae0f0146fa736a6427eb1180805717ce8a78e
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484976"
---
# <a name="align-controls"></a>对齐控件

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

以下过程显示如何对齐控件：

## <a name="to-align-groups-of-controls"></a>若要对齐控件组

1. [选择的控件](../windows/selecting-multiple-controls.md)你想要保持一致。 请务必选择你想要首先将主导控件的控件或将其设置为主导控件之前执行对齐方式或大小调整命令。

   最后一个控件组的位置取决于主导控件的位置。 选择主导控件的详细信息，请参阅[指定主导控件](../windows/specifying-the-dominant-control.md)。

1. 从**格式**菜单中，选择**对齐**，然后选择以下的对齐方式之一：

   - `Lefts`： 将所选的控件沿它们的左边对齐。

   - `Centers`： 将所选的控件水平沿其中心点。

   - `Rights`： 将所选的控件沿其右侧。

   - `Tops`： 将所选的控件沿上边缘。

   - `Middles`： 将所选的控件它们的中心点沿垂直方向对齐。

   - `Bottoms`： 将所选的控件沿其下边缘对齐。

## <a name="to-even-the-spacing-between-controls"></a>若要在控件之间的间距相等

**对话框**编辑器使您能够选择最外层控件之间均匀分配的空间控件。

1. 选择你想要重新排列的控件。

1. 从**格式**菜单中，选择**均匀隔开**，然后选择以下间距对齐方式之一：

   - `Across`： 空间之间均匀分配和选择最右边的控件的控件。

   - `Down`： 空间之间均匀分配最上面和最底部所选控件的控件。

## <a name="to-center-controls-in-a-dialog-box"></a>若要使控件在对话框内居中

1. 选择你想要重新排列的控件。

1. 从**格式**菜单中，选择**在对话框内居中**，然后选择以下的排列方式之一：

   - `Vertical`： 使控件在对话框中垂直居中。

   - `Horizontal`： 使控件在对话框中水平居中。

## <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>若要排列普通按钮沿右侧或底部的对话框

1. 选择一个或多个推送按钮。

1. 从**格式**菜单中，选择**排列按钮**，然后选择以下的排列方式之一：

   - `Right`： 对齐普通按钮的对话框中的右边缘。

   - `Bottom`: 对话框中的下边缘沿对齐普通按钮。

       如果选择不是普通按钮控件，其位置不受影响。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框上的控件排列](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)