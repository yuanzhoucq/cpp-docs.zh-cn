---
title: 动画控件发送的通知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 68ede3bc55669a29eef192d38b29b8c1ab433e4b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508014"
---
# <a name="notifications-sent-by-animation-controls"></a>动画控件发送的通知

动画控件 ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) 发送两种不同类型的通知消息。 以[WM_COMMAND](/windows/win32/menurc/wm-command)消息的形式发送通知。

动画控件开始播放剪辑时, 会发送[ACN_START](/windows/win32/Controls/acn-start)消息。 当动画控件完成或停止播放剪辑时, 将发送[ACN_STOP](/windows/win32/Controls/acn-stop)消息。

## <a name="see-also"></a>请参阅

[使用 CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
