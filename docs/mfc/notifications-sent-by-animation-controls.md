---
title: "动画控件发送的通知 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c57a33bf4b13397d4f296ef4e5aa8e137c2d3594
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="notifications-sent-by-animation-controls"></a>动画控件发送的通知
动画控件 ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) 发送两个不同类型的通知消息。 通知发送的窗体[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息。  
  
 [ACN_START](http://msdn.microsoft.com/library/windows/desktop/bb761891)消息在动画控件已开始播放剪辑时发送。 [ACN_STOP](http://msdn.microsoft.com/library/windows/desktop/bb761893)消息在动画控件已完成或停止播放剪辑时发送。  
  
## <a name="see-also"></a>请参阅  
 [使用 CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [控件](../mfc/controls-mfc.md)

