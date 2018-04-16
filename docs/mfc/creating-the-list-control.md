---
title: "创建列表控件 |Microsoft 文档"
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
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85afbe49943e06a66cf2fa914cc87f07b0fa8c52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-list-control"></a>创建列表控件
如何控制列表 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 创建取决于是否你直接使用该控件，或使用类[CListView](../mfc/reference/clistview-class.md)相反。 如果你使用`CListView`，该框架构造该视图作为其文档/视图创建序列的一部分。 创建列表视图创建列表控件也 （二者是相同的操作）。 在视图中的创建控件[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数。 在这种情况下，控件可供你添加项，通过调用[GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl)。  
  
### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>若要在对话框中直接使用 CListCtrl  
  
1.  在对话框编辑器中，将添加到对话框模板资源的列表控件。 指定其控件 ID。  
  
2.  使用[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)若要添加的类型的成员变量`CListCtrl`的控件属性。 您可以使用此成员调用 `CListCtrl` 成员函数。  
  
3.  使用属性窗口映射对话框类中的处理程序函数，对于任何列表控件通知消息你需要处理 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。  
  
4.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，设置的样式`CListCtrl`。 请参阅[更改列表控件样式](../mfc/changing-list-control-styles.md)。 尽管你以后可以更改视图，这将确定"视图"，在控件中，获取的类型。  
  
### <a name="to-use-clistctrl-in-a-nondialog-window"></a>要在非对话框窗口中使用 CListCtrl  
  
1.  在视图或窗口类中定义控件。  
  
2.  调用控件的[创建](../mfc/reference/clistctrl-class.md#create)成员函数，可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)中进行，父窗口的[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数 （如果您是将控件子类化）。 设置控件的样式。  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)

