---
title: 创建日期和时间选取器控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce7c987bf1284d0287cd0206572209d7ae2d0b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342129"
---
# <a name="creating-the-date-and-time-picker-control"></a>创建日期和时间选择器控件
日期和时间选取器控件的创建方式取决于您是使用控件在对话框中还是在非对话框窗口中创建它。  
  
### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>若要在对话框中直接使用 CDateTimeCtrl  
  
1.  在对话框编辑器中，将添加到对话框模板资源的日期和时间选取器控件。 指定其控件 ID。  
  
2.  指定任何所需，使用日期和时间选取器控件的属性对话框中的样式。  
  
3.  使用[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)若要添加的类型的成员变量[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)的控件属性。 您可以使用此成员调用 `CDateTimeCtrl` 成员函数。  
  
4.  使用属性窗口将在任何日期时间选取器控件的对话框类的处理程序函数映射[通知](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md)需要处理的消息 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。  
  
5.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，设置为任何其他样式`CDateTimeCtrl`对象。  
  
### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>要在非对话框窗口中使用 CDateTimeCtrl  
  
1.  声明中的视图或窗口类的控件。  
  
2.  调用控件的[创建](../mfc/reference/ctabctrl-class.md#create)成员函数，可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)中进行，父窗口的[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数 （如果您是将控件子类化）。 设置控件的样式。  
  
## <a name="see-also"></a>请参阅  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控件](../mfc/controls-mfc.md)

