---
title: 处理列表控件中的通知消息 |Microsoft 文档
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
ms.openlocfilehash: c5412bbf1fcb7e139394b9563965244080e5c179
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932076"
---
# <a name="processing-notification-messages-in-list-controls"></a>处理列表控件中的通知消息
当用户单击列标题时，拖动图标，编辑标签，依次类推，列表控件 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 将通知消息发送到其父窗口。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户单击列标题时，您可能要根据单击的列内容对项进行排序，与在 Microsoft Outlook 中一样。  
  
 从列表控件视图或对话框类中的进程 WM_NOTIFY 消息。 使用属性窗口创建[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)通过 switch 语句的处理程序函数基于正在处理的通知消息。  
  
 列表控件可以向其父窗口发送通知的列表，请参阅[列表视图控件参考](http://msdn.microsoft.com/library/windows/desktop/bb774737)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)

