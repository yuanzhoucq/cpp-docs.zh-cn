---
title: "创建日期和时间选取器控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e9c0b99f42bef162ed3c571e19630f9227a8504e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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

