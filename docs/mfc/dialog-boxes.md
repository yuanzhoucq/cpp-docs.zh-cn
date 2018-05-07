---
title: 对话框 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c8de283d81aa9d260b891f285f06555dc67895f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="dialog-boxes"></a>对话框
适用于 Windows 的应用程序经常与用户通过对话框通信。 类[CDialog](../mfc/reference/cdialog-class.md)提供了接口管理对话框中，Visual c + + 对话框编辑器可以轻松地设计对话框和创建对话框模板资源，并代码向导简化的初始化的过程和正在验证的控件在对话框中，收集用户输入的值。  
  
 对话框包含控件，包括：  
  
-   Windows 公共控件如编辑框、 按键，列表框、 组合框、 树控件、 列表控件和进度指示器。  
  
-   ActiveX 控件。  
  
-   所有者描述的控件： 你将负责在对话框框中绘制的控件。  
  
 大多数对话框是有模式对话框，即要求用户在使用任何其他部分的程序之前关闭对话框。 但可以创建无模式对话框框中，可让用户对话框处于打开状态时，与其他 windows 协作。 MFC 支持这两种类型的对话框中，与类`CDialog`。 控件排列和使用对话框模板资源，使用创建管理[对话框编辑器](../windows/dialog-editor.md)。  
  
 [属性表](../mfc/property-sheets-mfc.md)，也称为选项卡上显示对话框，是包含的不同对话框控件"页"对话框。 每页有顶部的"选项卡"中的文件文件夹。 单击选项卡可将该页调到对话框中的靠前。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [示例：通过菜单命令显示对话框](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)  
  
-   [框架中的对话框组件](../mfc/dialog-box-components-in-the-framework.md)  
  
-   [模式和无模式对话框](../mfc/modal-and-modeless-dialog-boxes.md)  
  
-   [属性表和属性页](../mfc/property-sheets-and-property-pages-mfc.md)在对话框中  
  
-   [创建对话框资源](../mfc/creating-the-dialog-resource.md)  
  
-   [使用代码向导创建对话框类](../mfc/creating-a-dialog-class-with-code-wizards.md)  
  
-   [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)  
  
-   [对话框数据交换 (DDX) 和验证 (DDV)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [对在对话框中的控件类型安全访问](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [将 Windows 消息映射到您的类](../mfc/mapping-windows-messages-to-your-class.md)  
  
-   [经常重写的成员函数](../mfc/commonly-overridden-member-functions.md)  
  
-   [经常添加的成员函数](../mfc/commonly-added-member-functions.md)  
  
-   [通用对话框类](../mfc/common-dialog-classes.md)  
  
-   [OLE 中的对话框](../mfc/dialog-boxes-in-ole.md)  
  
-   创建其用户界面为对话框中的应用程序： 请参阅[CMNCTRL1](../visual-cpp-samples.md)或[CMNCTRL2](../visual-cpp-samples.md)示例程序。 应用程序向导提供了此选项也。  
  
-   [示例](../mfc/dialog-sample-list.md)  
  
## <a name="see-also"></a>请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)
