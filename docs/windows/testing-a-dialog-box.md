---
title: 设计对话框 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
ms.openlocfilehash: 4a879f6bb1cdcd4b4897e510fb21d04500dfd3f2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742682"
---
# <a name="designing-a-dialog-box-c"></a>设计对话框 （c + +）

位置和大小的 c + + 对话框中，和位置中，控件的大小以对话框单元为单位测量。 当选择 Visual Studio 状态栏的右下角显示各个控件和对话框中的值。

当您设计对话框中时，还可以模拟并测试其运行时行为，而无需编译您的程序。 在此模式中，您可以：

- 键入文本、从组合框列表中选择、打开或关闭选项，以及选择命令。

- 测试 Tab 键顺序。

- 测试控件的分组，如单选按钮和复选框。

- 在对话框中测试控件的键盘快捷键。

   > [!NOTE]
   > 与使用向导生成的对话框代码的连接不包括在此模拟中。

当测试对话框时，它通常显示在与主程序窗口相对的位置。 如果你已设置对话框的**Absolute Align**属性设置为**True**，对话框会显示在相对于屏幕的左上角的位置。

有关如何将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)。

## <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>若要指定的位置和大小的对话框

有三个属性，您可以在设置[属性窗口](/visualstudio/ide/reference/properties-window)指定对话框将出现在屏幕上。 **Center**属性是一个布尔值; 如果将值设置为**True**，对话框中将始终显示在屏幕的中心。 如果设置为**False**，然后，可以设置**XPos**并**YPos**属性来显式定义在屏幕上将显示此对话框。 位置属性是从查看区域，该常数定义为左上角的偏移量的值`{X=0, Y=0}`。 位置也基于**Absolute Align**属性： 如果**True**，坐标是相对于屏幕; 如果**False**，坐标都相对于对话框所有者的窗口。

## <a name="to-test-a-dialog-box"></a>测试对话框

1. 当**对话框中**编辑器为活动窗口时，在菜单栏上的，选择**格式** > **测试对话框**。

1. 若要结束此模拟，按**Esc**，或只需选择**关闭**要测试的对话框中的按钮。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[对话框编辑器](../windows/dialog-editor.md)<br/>
[显示或隐藏对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)