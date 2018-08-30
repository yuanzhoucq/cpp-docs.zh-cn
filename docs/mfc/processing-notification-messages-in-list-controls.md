---
title: 处理列表控件中的通知消息 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3362074ce0f8d4d7a3a3463d22f9089f847e747d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208705"
---
# <a name="processing-notification-messages-in-list-controls"></a>处理列表控件中的通知消息
当用户单击列标题，拖动图标，编辑标签和等等，列表控件 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 到其父窗口发送通知消息。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户单击列标题时，您可能要根据单击的列内容对项进行排序，与在 Microsoft Outlook 中一样。  
  
 从视图或对话框类中的列表控件的处理 WM_NOTIFY 消息。 使用属性窗口来创建[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)使用 switch 语句的处理程序函数基于正在处理通知消息。  
  
 列表控件可以向其父窗口发送的通知的列表，请参阅[列表视图控件参考](/windows/desktop/Controls/list-view-control-reference)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)

