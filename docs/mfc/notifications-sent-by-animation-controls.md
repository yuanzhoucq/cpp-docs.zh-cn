---
title: 动画控件发送的通知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 2a736e4315091b1b26daceb4fe0ce9672ab33ff6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62238304"
---
# <a name="notifications-sent-by-animation-controls"></a>动画控件发送的通知

动画控件 ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) 发送两个不同类型的通知消息。 中的形式发送的通知[WM_COMMAND](/windows/desktop/menurc/wm-command)消息。

[ACN_START](/windows/desktop/Controls/acn-start)动画控件已开始播放剪辑时发送消息。 [ACN_STOP](/windows/desktop/Controls/acn-stop)动画控件已完成或停止播放剪辑时发送消息。

## <a name="see-also"></a>请参阅

[使用 CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
