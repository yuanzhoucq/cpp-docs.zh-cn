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
ms.openlocfilehash: 75b19033a31d707fcc87c1b5c824acffca725c96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441960"
---
# <a name="processing-tab-control-notification-messages"></a>处理选项卡控件通知消息

当用户单击选项卡或按钮、 选项卡控件 ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) 到其父窗口发送通知消息。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户单击一个选项卡，您可以预设之前显示该页面上的控件数据。

从视图或对话框类中的选项卡控件的处理 WM_NOTIFY 消息。 使用属性窗口来创建[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)使用 switch 语句的处理程序函数基于正在处理通知消息。 选项卡控件可以向其父窗口发送的通知的列表，请参阅**通知**一部分[选项卡控件引用](https://msdn.microsoft.com/library/windows/desktop/bb760548)Windows SDK 中。

## <a name="see-also"></a>请参阅

[使用 CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

