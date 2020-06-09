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
ms.openlocfilehash: da6a2eca7c2366e519b9bf2e809b042dc3ee2e50
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616873"
---
# <a name="dialog-boxes"></a>对话框

适用于 Windows 的应用程序经常通过对话框与用户通信。 类[CDialog](reference/cdialog-class.md)提供了一个用于管理对话框的界面，Visual C++ 对话框编辑器使您能够轻松地设计对话框和创建其对话框模板资源，代码向导可简化在对话框中初始化和验证控件以及收集用户输入的值的过程。

对话框包含控件，其中包括：

- Windows 公共控件，如编辑框、按钮、列表框、组合框、树控件、列表控件和进度指示器。

- ActiveX 控件。

- 所有者描述的控件：你负责在对话框中进行绘制的控件。

大多数对话框都是模式模式，这要求用户在使用程序的任何其他部分之前关闭对话框。 但可以创建无模式对话框，使用户能够在对话框处于打开状态时使用其他窗口。 MFC 同时支持这两种对话框和类 `CDialog` 。 控件是使用对话框[编辑器](../windows/dialog-editor.md)创建的，并使用对话框模板资源进行排列和管理。

[属性表](property-sheets-mfc.md)，也称为选项卡对话框，是包含不同对话框控件的 "页" 的对话框。 每一页的顶部都有一个文件夹 "选项卡"。 单击某个选项卡会将该页面带入对话框前面。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [示例：通过菜单命令显示对话框](example-displaying-a-dialog-box-via-a-menu-command.md)

- [框架中的对话框组件](dialog-box-components-in-the-framework.md)

- [模式和非模式对话框](modal-and-modeless-dialog-boxes.md)

- 对话框中的[属性表和属性页](property-sheets-and-property-pages-mfc.md)

- [创建对话框资源](creating-the-dialog-resource.md)

- [使用代码向导创建对话框类](creating-a-dialog-class-with-code-wizards.md)

- [在 MFC 中使用对话框](life-cycle-of-a-dialog-box.md)

- [对话框数据交换（DDX）和验证（DDV）](dialog-data-exchange-and-validation.md)

- [对对话框中的控件进行类型安全的访问](type-safe-access-to-controls-in-a-dialog-box.md)

- [将 Windows 消息映射到类](mapping-windows-messages-to-your-class.md)

- [经常重写的成员函数](commonly-overridden-member-functions.md)

- [经常添加的成员函数](commonly-added-member-functions.md)

- [通用对话框类](common-dialog-classes.md)

- [OLE 中的对话框](dialog-boxes-in-ole.md)

- 创建一个应用程序，该应用程序的用户界面为对话框：请参阅[CMNCTRL1](../overview/visual-cpp-samples.md)或[CMNCTRL2](../overview/visual-cpp-samples.md)示例程序。 应用程序向导也会提供此选项。

- [示例](dialog-sample-list.md)

## <a name="see-also"></a>另请参阅

[用户界面元素](user-interface-elements-mfc.md)
