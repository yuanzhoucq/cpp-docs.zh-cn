---
title: 处理 Rebar 控件中的通知消息 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4532206be5787266df470dedceda0880222b675f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438491"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>处理 Rebar 控件中的通知消息

在 rebar 控件的父类中，为所有需要处理的 rebar 控件 (`OnChildNotify`) 通知消息创建一个带有 switch 语句的 `CReBarCtrl` 处理程序函数。 当用户在 rebar 控件上拖动对象、更改 rebar 带区的布局、从 rebar 控件中删除带区等时，将向其父窗口发送通知。

可通过 rebar 控件对象发送以下通知消息：

- RBN_AUTOSIZE，由 rebar 控件 （使用 RBS_AUTOSIZE 样式创建） 发送当 rebar 自动调整自身大小。

- 当用户开始拖动带区的 rebar 控件发送 RBN_BEGINDRAG。

- RBN_CHILDSIZE，由 rebar 控件带区的子窗口调整大小时发送。

- RBN_DELETEDBAND，由 rebar 控件删除带区后发送。

- RBN_DELETINGBAND，由 rebar 控件即将删除带区时发送。

- RBN_ENDDRAG，由 rebar 控件用户停止拖动带区时发送。

- RBN_GETOBJECT，由 rebar 控件 （使用 RBS_REGISTERDROP 样式创建） 发送时将对象拖控件中的带。

- RBN_HEIGHTCHANGE，由 rebar 控件窗体的高度已更改时发送。

- RBN_LAYOUTCHANGED，由 rebar 控件在用户更改控件的带区布局时发送。

这些通知的详细信息，请参阅[Rebar 控件参考](https://msdn.microsoft.com/library/windows/desktop/bb774375)Windows SDK 中。

## <a name="see-also"></a>请参阅

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

