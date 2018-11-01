---
title: 处理列表控件中的通知消息
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: 427abe5259334588b566656abd70acf22b923809
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490085"
---
# <a name="processing-notification-messages-in-list-controls"></a>处理列表控件中的通知消息

当用户单击列标题，拖动图标，编辑标签和等等，列表控件 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 到其父窗口发送通知消息。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户单击列标题时，您可能要根据单击的列内容对项进行排序，与在 Microsoft Outlook 中一样。

从视图或对话框类中的列表控件的处理 WM_NOTIFY 消息。 使用属性窗口来创建[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)使用 switch 语句的处理程序函数基于正在处理通知消息。

列表控件可以向其父窗口发送的通知的列表，请参阅[列表视图控件参考](/windows/desktop/Controls/list-view-control-reference)Windows SDK 中。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

