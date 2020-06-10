---
title: 动画控件发送的通知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: e9e5b94736de44d5cfeef81f5b78a759df3b8aa0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619914"
---
# <a name="notifications-sent-by-animation-controls"></a>动画控件发送的通知

动画控件（[CAnimateCtrl](reference/canimatectrl-class.md)）发送两种不同类型的通知消息。 将以[WM_COMMAND](/windows/win32/menurc/wm-command)消息的形式发送通知。

当动画控件开始播放剪辑时，将发送[ACN_START](/windows/win32/Controls/acn-start)消息。 当动画控件完成或停止播放剪辑时，将发送[ACN_STOP](/windows/win32/Controls/acn-stop)消息。

## <a name="see-also"></a>另请参阅

[使用 CAnimateCtrl](using-canimatectrl.md)<br/>
[控件](controls-mfc.md)
