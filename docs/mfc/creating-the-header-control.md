---
title: "创建标题控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c47e458d4cd6e9df556eef5e1f61806633208011
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="creating-the-header-control"></a>创建标题控件
标头控件不可直接在对话框编辑器中 （尽管你可以添加一个列表控件，其中包括标头控件）。  
  
### <a name="to-put-a-header-control-in-a-dialog-box"></a>若要将标头控件放在对话框中  
  
1.  手动嵌入类型的成员变量[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)对话框类中。  
  
2.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)、 创建和设置的样式`CHeaderCtrl`、 将其，并将其显示。  
  
3.  将项添加到标头控件。  
  
4.  使用属性窗口映射对话框类中的处理程序函数，对于任何标头控件通知消息你需要处理 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。  
  
### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>若要将标头控件放在视图 (不 CListView)  
  
1.  嵌入[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)视图类中的对象。  
  
2.  设置样式、 定位和的视图中显示标头控件窗口[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)成员函数。  
  
3.  将项添加到标头控件。  
  
4.  使用属性窗口映射的 view 类中的处理程序函数，对于任何标头控件通知消息你需要处理 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。  
  
 在任一情况下，在创建视图或对话框对象时创建的嵌入的控件对象。 然后必须调用[CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create)创建控件窗口。 若要定位该控件，调用[CHeaderCtrl::Layout](../mfc/reference/cheaderctrl-class.md#layout)以确定控件的初始大小和位置和[SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos)设置所需的位置。 然后添加项中所述[将项添加到标头控件](../mfc/adding-items-to-the-header-control.md)。  
  
 有关详细信息，请参阅[创建标头控件](http://msdn.microsoft.com/library/windows/desktop/bb775238)Windows SDK 中。  
  
## <a name="see-also"></a>另请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控件](../mfc/controls-mfc.md)

