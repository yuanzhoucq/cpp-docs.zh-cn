---
title: 使用 CAnimateCtrl |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CAnimateCtrl
dev_langs:
- C++
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5685d6aed00cd57f4329b3865f96fa75226d7cf6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381613"
---
# <a name="using-canimatectrl"></a>使用 CAnimateCtrl
动画控件，由类表示[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)，是一个窗口，显示音频视频交错 (AVI) 格式的剪辑-标准 Windows 视频/音频格式。 AVI 剪辑是一系列位图帧，与电影相似。  
  
 由于显示 AVI 剪辑时线程会继续执行，动画控件的一个常见用途是在较长的操作期间指示系统活动。 例如，当系统搜索文件时，“Windows 查找”对话框会显示一个移动的放大镜。  
  
 动画控件只能播放简单的 AVI 剪辑，不支持声音。 (有关限制的完整列表，请参阅[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)。)由于动画控件的功能受到严重限制并且随时会更改，因此如果您需要可提供多媒体播放和/或录制功能的控件，则应使用替代工具（如 MCIWnd 控件）。 有关 MCIWnd 控件的详细信息，请参阅多媒体文档。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [使用动画控件](../mfc/using-an-animation-control.md)  
  
-   [动画控件发送的通知](../mfc/notifications-sent-by-animation-controls.md)  
  
## <a name="see-also"></a>请参阅  
 [控件](../mfc/controls-mfc.md)

