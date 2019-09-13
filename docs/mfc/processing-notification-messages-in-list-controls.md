---
title: 处理列表控件中的通知消息
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: 92111e3e0a4869ca06b89d2d18d38aab9f10ab7d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908097"
---
# <a name="processing-notification-messages-in-list-controls"></a>处理列表控件中的通知消息

当用户单击列标题、拖动图标、编辑标签等操作时，列表控件（[CListCtrl](../mfc/reference/clistctrl-class.md)）会向其父窗口发送通知消息。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户单击列标题时，您可能要根据单击的列内容对项进行排序，与在 Microsoft Outlook 中一样。

处理视图或对话框类中列表控件的 WM_NOTIFY 消息。 使用[类向导](reference/mfc-class-wizard.md)创建[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)处理程序函数，其中包含基于正在处理的通知消息的 switch 语句。

有关列表控件可发送到其父窗口的通知的列表，请参阅 Windows SDK 中的[列表视图控制引用](/windows/win32/Controls/list-view-control-reference)。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
