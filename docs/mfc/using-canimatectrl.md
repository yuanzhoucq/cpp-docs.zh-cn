---
title: 使用 CAnimateCtrl
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: b967cc6dde6b4f639ef081b3821f6a7e5a2fe295
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287435"
---
# <a name="using-canimatectrl"></a>使用 CAnimateCtrl

动画控件，表示由类[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)，是音频视频交错 (AVI) 格式显示剪辑的窗口 — 标准 Windows 视频/音频格式。 AVI 剪辑是一系列位图帧，与电影相似。

由于显示 AVI 剪辑时线程会继续执行，动画控件的一个常见用途是在较长的操作期间指示系统活动。 例如，当系统搜索文件时，“Windows 查找”对话框会显示一个移动的放大镜。

动画控件只能播放简单的 AVI 剪辑，不支持声音。 (有关限制的完整列表，请参阅[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)。)由于动画控件的功能受到严重限制并且随时会更改，因此如果您需要可提供多媒体播放和/或录制功能的控件，则应使用替代工具（如 MCIWnd 控件）。 有关 MCIWnd 控件的详细信息，请参阅多媒体文档。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [使用动画控件](../mfc/using-an-animation-control.md)

- [动画控件发送的通知](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>请参阅

[控件](../mfc/controls-mfc.md)
