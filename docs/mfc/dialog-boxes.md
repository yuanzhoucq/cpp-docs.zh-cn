---
title: 对话框
ms.date: 11/04/2016
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
ms.openlocfilehash: 32a8f8784459338131d4893f25d8798f8031b68b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778489"
---
# <a name="dialog-boxes"></a>对话框

通过对话框用户适用于 Windows 应用程序频繁地通信。 类[CDialog](../mfc/reference/cdialog-class.md)管理对话框，Visual c + + 对话框编辑器轻松地设计对话框和创建它们的对话框模板资源，并且代码向导简化的初始化过程提供了一个接口和正在验证的控件在对话框中，收集用户输入的值。

对话框包含控件，包括：

- Windows 公共控件如编辑框、 普通按钮、 列表框、 组合框、 树控件、 列表控件和进度指示器等。

- ActiveX 控件。

- 所有者描述的控件： 你有责任在对话框中绘制的控件。

大多数对话框都是模式，这要求用户使用该程序的任何其他部分之前关闭该对话框。 但可以创建无模式对话框，可让用户使用其他窗口对话框的处于打开状态时。 MFC 支持这两种类型的对话框类`CDialog`。 控件的排列和使用与创建的对话框模板资源管理[对话框编辑器](../windows/dialog-editor.md)。

[属性表](../mfc/property-sheets-mfc.md)，也称为选项卡对话框，是包含的不同对话框控件"页"对话框。 每个页面有一个文件文件夹顶部的"选项卡"。 单击一个选项卡将该页放到对话框中的前面。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [示例:显示一个对话框，通过菜单命令](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)

- [框架中的对话框组件](../mfc/dialog-box-components-in-the-framework.md)

- [模式和无模式对话框](../mfc/modal-and-modeless-dialog-boxes.md)

- [属性表和属性页](../mfc/property-sheets-and-property-pages-mfc.md)在对话框中

- [创建对话框资源](../mfc/creating-the-dialog-resource.md)

- [使用代码向导创建对话框类](../mfc/creating-a-dialog-class-with-code-wizards.md)

- [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

- [对话框数据交换 (DDX) 和验证 (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [对对话框中的控件类型安全访问](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Windows 消息映射到您的类](../mfc/mapping-windows-messages-to-your-class.md)

- [经常重写的成员函数](../mfc/commonly-overridden-member-functions.md)

- [经常添加的成员函数](../mfc/commonly-added-member-functions.md)

- [通用对话框类](../mfc/common-dialog-classes.md)

- [OLE 中的对话框](../mfc/dialog-boxes-in-ole.md)

- 创建应用程序用户界面是一个对话框： 请参阅[CMNCTRL1](../overview/visual-cpp-samples.md)或[CMNCTRL2](../overview/visual-cpp-samples.md)示例程序。 应用程序向导提供了此选项。

- [示例](../mfc/dialog-sample-list.md)

## <a name="see-also"></a>请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)
