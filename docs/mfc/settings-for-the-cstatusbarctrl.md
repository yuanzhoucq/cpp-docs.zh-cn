---
title: CStatusBarCtrl 的设置
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: dd7c68d6721c48f751c04437e43c8770f6ec5736
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365382"
---
# <a name="settings-for-the-cstatusbarctrl"></a>CStatusBarCtrl 的设置

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)状态窗口的默认位置位于父窗口的底部，但您可以指定CCS_TOP样式，使其显示在父窗口的工作区的顶部。

您可以指定SBARS_SIZEGRIP样式，以在`CStatusBarCtrl`状态窗口的右端包括大小调整夹。 大小调整手柄类似于大小调整边框；它是用户可以通过单击和拖动来重设父窗口大小的矩形区域。

> [!NOTE]
> 如果将CCS_TOP和SBARS_SIZEGRIP样式组合在一起，则即使系统在状态窗口中绘制，生成的大小调整夹点也不会正常工作。

状态窗口的窗口过程将自动设置控件窗口的初始大小和位置。 宽度与父窗口工作区的一样。 高度基于实际选入状态窗口设备上下文的字体的度量值和窗口边框的宽度。

窗口过程在接收WM_SIZE消息时自动调整状态窗口的大小。 通常，当父窗口的大小发生变化时，父窗口向状态窗口发送WM_SIZE消息。

您可以通过调用[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)来设置状态窗口绘图区域的最小高度，指定最小高度（以像素为单位）。 绘图区不包括窗口边框。

通过调用[GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders)来检索状态窗口边框的宽度。 此成员函数包含指向三元素数组（将收到水平边框、垂直边框和矩形之间的边框的宽度）的指针。

## <a name="see-also"></a>另请参阅

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
