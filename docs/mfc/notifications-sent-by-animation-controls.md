---
title: 动画控件发送的通知 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb83fe6195c01c1e9dbcc2c00e43738af9ebc8e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386387"
---
# <a name="notifications-sent-by-animation-controls"></a>动画控件发送的通知

动画控件 ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) 发送两个不同类型的通知消息。 中的形式发送的通知[WM_COMMAND](/windows/desktop/menurc/wm-command)消息。

[ACN_START](/windows/desktop/Controls/acn-start)动画控件已开始播放剪辑时发送消息。 [ACN_STOP](/windows/desktop/Controls/acn-stop)动画控件已完成或停止播放剪辑时发送消息。

## <a name="see-also"></a>请参阅

[使用 CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

