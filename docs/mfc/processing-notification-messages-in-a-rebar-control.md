---
title: 处理 Rebar 控件中的通知消息
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: e1e1aaa5056b43f0dd23976fead94bc800163613
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625191"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>处理 Rebar 控件中的通知消息

在 rebar 控件的父类中，为所有需要处理的 rebar 控件 (`OnChildNotify`) 通知消息创建一个带有 switch 语句的 `CReBarCtrl` 处理程序函数。 当用户在 rebar 控件上拖动对象、更改 rebar 带区的布局、从 rebar 控件中删除带区等时，将向其父窗口发送通知。

可通过 rebar 控件对象发送以下通知消息：

- 当 rebar 自动调整自身的大小时，由 rebar 控件发送 RBN_AUTOSIZE （使用 RBS_AUTOSIZE 样式创建）。

- 当用户开始拖动带区时，由 rebar 控件发送 RBN_BEGINDRAG。

- 当调整带区子窗口的大小时，由 rebar 控件发送 RBN_CHILDSIZE。

- 删除带区后，由 rebar 控件发送 RBN_DELETEDBAND。

- 当要删除带区时，由 rebar 控件发送 RBN_DELETINGBAND。

- 当用户停止拖动带区时，由 rebar 控件发送 RBN_ENDDRAG。

- 将对象拖到控件中的带区上时，由 rebar 控件发送的 RBN_GETOBJECT （使用 RBS_REGISTERDROP 样式创建）。

- RBN_HEIGHTCHANGE 在其高度更改时由 rebar 控件发送。

- 当用户更改控件带区的布局时，由 rebar 控件发送 RBN_LAYOUTCHANGED。

有关这些通知的详细信息，请参阅中的[Rebar 控件引用](/windows/win32/controls/rebar-control-reference)Windows SDK。

## <a name="see-also"></a>另请参阅

[使用 CReBarCtrl](using-crebarctrl.md)<br/>
[控件](controls-mfc.md)
