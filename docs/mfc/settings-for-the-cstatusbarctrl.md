---
title: CStatusBarCtrl 的设置 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1dde1f005e53aff7ebe505d1ce619bf5c94410f8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955451"
---
# <a name="settings-for-the-cstatusbarctrl"></a>CStatusBarCtrl 的设置
默认位置[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)状态窗口是父窗口的底部，但你可以指定 CCS_TOP 样式让其显示在父窗口工作区的顶部。  
  
 你可以指定要包括的最右侧大小调整手柄的 SBARS_SIZEGRIP 样式`CStatusBarCtrl`状态窗口。 大小调整手柄类似于大小调整边框；它是用户可以通过单击和拖动来重设父窗口大小的矩形区域。  
  
> [!NOTE]
>  如果你合并 CCS_TOP 和 SBARS_SIZEGRIP 样式，即使系统将其绘制在状态窗口中不起作用生成的大小调整手柄。  
  
 状态窗口的窗口过程将自动设置控件窗口的初始大小和位置。 宽度与父窗口工作区的一样。 高度基于实际选入状态窗口设备上下文的字体的度量值和窗口边框的宽度。  
  
 窗口过程自动调整状态窗口的大小，在收到 WM_SIZE 消息。 通常情况下，当父窗口的大小发生更改，父级将 WM_SIZE 消息发送到状态窗口。  
  
 你可以通过调用设置状态窗口绘图区的最小高度[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)，以像素为单位指定最小高度。 绘图区不包括窗口边框。  
  
 通过调用检索状态窗口边框的宽度[GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders)。 此成员函数包含指向三元素数组（将收到水平边框、垂直边框和矩形之间的边框的宽度）的指针。  
  
## <a name="see-also"></a>请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

