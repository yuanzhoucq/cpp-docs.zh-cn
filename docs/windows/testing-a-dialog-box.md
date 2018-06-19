---
title: 测试对话框 |Microsoft 文档
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
- dialog boxes, testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57bb9e827caae0e328971077d902673f2428c80b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889534"
---
# <a name="testing-a-dialog-box"></a>测试对话框
当您设计对话框时，无需编译程序即可模拟并测试其运行时行为。 在此模式中，您可以：  
  
-   键入文本、从组合框列表中选择、打开或关闭选项，以及选择命令。  
  
-   测试 Tab 键顺序。  
  
-   测试控件的分组，如单选按钮和复选框。  
  
-   在对话框中测试控件的键盘快捷键。  
  
    > [!NOTE]
    >  与使用向导生成的对话框代码的连接不包括在此模拟中。  
  
 当测试对话框时，它通常显示在与主程序窗口相对的位置。 如果已经将对话框的 Absolute Align 属性设置为 True，则对话框显示在相对于屏幕左上角的位置。  
  
### <a name="to-test-a-dialog-box"></a>测试对话框  
  
1.  当对话框编辑器为活动窗口时，在菜单栏上，选择 **“格式”**、 **“测试对话框”**。  
  
2.  若要结束此模拟，请按 Esc，或选择正在测试的对话框中的 **“关闭”** 按钮。  
  
 有关如何将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)。  
  
 要求  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [在对话框中的控件](../windows/controls-in-dialog-boxes.md)   
 [对话框编辑器](../windows/dialog-editor.md)   
 [显示或隐藏对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)

