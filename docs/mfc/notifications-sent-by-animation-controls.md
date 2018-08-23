---
title: 动画控件发送的通知 |Microsoft 文档
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
ms.openlocfilehash: c1696389ce3dc40c5d02ec660ebaeb6bf3e6c3ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345233"
---
# <a name="notifications-sent-by-animation-controls"></a>动画控件发送的通知
动画控件 ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) 发送两个不同类型的通知消息。 通知发送的窗体[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息。  
  
 [ACN_START](http://msdn.microsoft.com/library/windows/desktop/bb761891)消息在动画控件已开始播放剪辑时发送。 [ACN_STOP](http://msdn.microsoft.com/library/windows/desktop/bb761893)消息在动画控件已完成或停止播放剪辑时发送。  
  
## <a name="see-also"></a>请参阅  
 [使用 CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [控件](../mfc/controls-mfc.md)

