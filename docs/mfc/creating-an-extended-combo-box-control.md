---
title: 创建扩展的组合框控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c6a891aeadf2fa8366eec52a967e13776db6523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="creating-an-extended-combo-box-control"></a>创建扩展组合框控件
如何创建扩展的组合框控件取决于你是要使用控件在对话框中，还是要在非对话框窗口中创建。  
  
### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>若要在对话框中直接使用 CComboBoxEx  
  
1.  在对话框编辑器中，将的扩展组合框控件添加到对话框模板资源。 指定其控件 ID。  
  
2.  指定任何所需，使用属性对话框中的扩展的组合框控件样式。  
  
3.  使用[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)若要添加的类型的成员变量[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)的控件属性。 您可以使用此成员调用 `CComboBoxEx` 成员函数。  
  
4.  使用属性窗口将在需要以处理任何扩展的组合框控件通知消息的对话框类的处理程序函数映射 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。  
  
5.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，设置为任何其他样式`CComboBoxEx`对象。  
  
### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>要在非对话框窗口中使用 CComboBoxEx  
  
1.  在视图或窗口类中定义控件。  
  
2.  调用控件的[创建](../mfc/reference/ctabctrl-class.md#create)成员函数，可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)中进行，父窗口的[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数。 设置控件的样式。  
  
## <a name="see-also"></a>请参阅  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控件](../mfc/controls-mfc.md)

