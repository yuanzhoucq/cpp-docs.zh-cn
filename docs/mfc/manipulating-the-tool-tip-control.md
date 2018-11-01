---
title: 操作工具提示控件
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
ms.openlocfilehash: 2624f6c1da0e771b34d590d787c00e53ee6ff62e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625913"
---
# <a name="manipulating-the-tool-tip-control"></a>操作工具提示控件

`CToolTipCtrl` 类提供一组控制 `CToolTipCtrl` 对象的各种特性和工具提示窗口的成员函数。

初始、 弹出窗口中，并重新显示持续时间可以设置工具提示窗口并通过调用检索[GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime)并[SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime)。

使用以下函数更改工具提示窗口的外观：

- [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin)并[SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin)检索和设置工具提示边框和工具之间的宽度提示文本。

- [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth)并[SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth)检索和设置的最大宽度的工具提示窗口。

- [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor)并[SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor)检索和设置的背景色的工具提示窗口。

- [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor)并[SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor)检索和设置的文本颜色的工具提示窗口。

为了使工具提示控件通知重要消息，例如 WM_LBUTTONXXX 消息，必须将消息中继到工具提示控件。 对于此中继的最佳方法是调用[ctooltipctrl:: Relayevent](../mfc/reference/ctooltipctrl-class.md#relayevent)，请在`PreTranslateMessage`所有者窗口的函数。 以下示例演示了一种可能的方法（假定此工具提示控件名为 `m_ToolTip`）：

[!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

若要立即移除工具提示窗口，调用[弹出](../mfc/reference/ctooltipctrl-class.md#pop)成员函数。

## <a name="see-also"></a>请参阅

[使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

