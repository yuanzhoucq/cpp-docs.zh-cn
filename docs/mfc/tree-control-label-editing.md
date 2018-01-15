---
title: "树控件标签编辑 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03fb11c29b51b30b1aaffccbe3e999f1cefc3fbb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-label-editing"></a>树控件标签编辑
用户可以直接编辑树控件中的项的标签 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))，其**TVS_EDITLABELS**样式。 用户通过单击具有焦点的项的标签开始编辑。 应用程序开始编辑通过使用[EditLabel](../mfc/reference/ctreectrl-class.md#editlabel)成员函数。 树控件在编辑开始以及编辑取消或完成时发送通知。 当编辑完成时，您负责根据需要更新项的标签。  
  
 当标签编辑开始时，树控件将发送[TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506)通知消息。 通过处理此通知，您可以允许某些标签的编辑并阻止其他标签的编辑。 返回 0 将允许编辑，返回非零将阻止编辑。  
  
 当标签编辑取消或完成时，树控件将发送[TVN_ENDLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773515)通知消息。 `lParam`参数是的地址[NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418)结构。 **项**成员是[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456)结构，它标识项和包括的已编辑的文本。 您负责根据需要更新项的标签（可能在验证编辑过的字符串之后）。 **PszText**的成员`TV_ITEM`为 0，如果取消了编辑。  
  
 在标签编辑期间，通常以响应[TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506)通知消息，你可以获取指向用于标签编辑通过使用编辑控件[GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol)成员函数。 你可以调用编辑控件的[SetLimitText](../mfc/reference/cedit-class.md#setlimittext)成员函数，以限制用户可以输入的文本或子类以截获和丢弃无效字符的编辑控件的量。 但请注意，仅显示编辑控件*后* **TVN_BEGINLABELEDIT**发送。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

