---
title: 测试对话框 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ca5e8cfc2a08b01d7917d540c61e04837169a457
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438595"
---
# <a name="testing-a-dialog-box-c"></a>测试对话框 （c + +）

当您设计对话框时，无需编译程序即可模拟并测试其运行时行为。 在此模式中，您可以：

- 键入文本、从组合框列表中选择、打开或关闭选项，以及选择命令。

- 测试 Tab 键顺序。

- 测试控件的分组，如单选按钮和复选框。

- 在对话框中测试控件的键盘快捷键。

   > [!NOTE]
   > 与使用向导生成的对话框代码的连接不包括在此模拟中。

当测试对话框时，它通常显示在与主程序窗口相对的位置。 如果你已设置对话框的**Absolute Align**属性设置为**True**，对话框会显示在相对于屏幕的左上角的位置。

### <a name="to-test-a-dialog-box"></a>测试对话框

1. 当**对话框中**编辑器为活动窗口时，在菜单栏上的，选择**格式** > **测试对话框**。

2. 若要结束此模拟，按**Esc**，或只需选择**关闭**正在测试的对话框中的按钮。

有关如何将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[对话框编辑器](../windows/dialog-editor.md)<br/>
[显示或隐藏对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)