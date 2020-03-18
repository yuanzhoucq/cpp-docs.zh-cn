---
title: 使用 CAnimateCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: 79c1a0111317514ef6fd68acd0c6a2ebdccc3ba4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447108"
---
# <a name="using-canimatectrl"></a>使用 CAnimateCtrl

由[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)类表示的动画控件是以音频视频交错（AVI）格式（标准 Windows 视频/音频格式）显示剪辑的窗口。 AVI 剪辑是一系列位图帧，与电影相似。

由于显示 AVI 剪辑时线程会继续执行，动画控件的一个常见用途是在较长的操作期间指示系统活动。 例如，当系统搜索文件时，“Windows 查找”对话框会显示一个移动的放大镜。

动画控件只能播放简单的 AVI 剪辑，不支持声音。 （有关限制的完整列表，请参阅[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)。）由于动画控件的功能受到严格限制并且可能会发生更改，因此，如果需要提供多媒体播放和/或录制功能的控件，则应使用 MCIWnd 控件等替代方法。 有关 MCIWnd 控件的详细信息，请参阅多媒体文档。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [使用动画控件](../mfc/using-an-animation-control.md)

- [动画控件发送的通知](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>另请参阅

[控件](../mfc/controls-mfc.md)
