---
title: 处理选项卡控件通知消息
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
ms.openlocfilehash: 97abde8285a3baf307df79fd97d4f9a379c8f58f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507834"
---
# <a name="processing-tab-control-notification-messages"></a>处理选项卡控件通知消息

当用户单击选项卡或按钮时, 选项卡控件 ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) 会向其父窗口发送通知消息。 如果您要在响应中做些什么，请处理这些消息。 例如, 当用户单击某个选项卡时, 您可能希望在显示页面之前预先预设控件上的控件数据。

处理视图或对话框类中的选项卡控件中的 WM_NOTIFY 消息。 使用属性窗口基于正在处理的通知消息使用 switch 语句创建[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)处理程序函数。 有关选项卡控件可以发送到其父窗口的通知的列表, 请参阅 Windows SDK 中[选项卡控件参考](/windows/win32/controls/tab-control-reference)的 "**通知**" 部分。

## <a name="see-also"></a>请参阅

[使用 CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
