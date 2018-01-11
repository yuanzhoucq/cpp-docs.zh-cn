---
title: "CStatusBarCtrl 的设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 814c12b13333d589cb568c5c637f0fa34956847e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="settings-for-the-cstatusbarctrl"></a>CStatusBarCtrl 的设置
默认位置[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)状态窗口是父窗口的底部，但你可以指定`CCS_TOP`样式让其出现在父窗口工作区的顶部。  
  
 你可以指定**SBARS_SIZEGRIP**以包括最右侧大小调整手柄的样式`CStatusBarCtrl`状态窗口。 大小调整手柄类似于大小调整边框；它是用户可以通过单击和拖动来重设父窗口大小的矩形区域。  
  
> [!NOTE]
>  如果合并`CCS_TOP`和**SBARS_SIZEGRIP**样式，生成的大小调整手柄不起作用即使系统将其绘制在状态窗口中也是如此。  
  
 状态窗口的窗口过程将自动设置控件窗口的初始大小和位置。 宽度与父窗口工作区的一样。 高度基于实际选入状态窗口设备上下文的字体的度量值和窗口边框的宽度。  
  
 窗口过程将在收到 `WM_SIZE` 消息后自动调整状态窗口的大小。 通常，当父窗口的大小发生更改时，父级将向状态窗口发送 `WM_SIZE` 消息。  
  
 你可以通过调用设置状态窗口绘图区的最小高度[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)，以像素为单位指定最小高度。 绘图区不包括窗口边框。  
  
 通过调用检索状态窗口边框的宽度[GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders)。 此成员函数包含指向三元素数组（将收到水平边框、垂直边框和矩形之间的边框的宽度）的指针。  
  
## <a name="see-also"></a>请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

