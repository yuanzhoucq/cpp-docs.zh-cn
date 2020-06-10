---
title: 操作工具提示控件
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
ms.openlocfilehash: 61bc35e8b19ba7645736b939acac6cdaa6cb7316
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622413"
---
# <a name="manipulating-the-tool-tip-control"></a>操作工具提示控件

`CToolTipCtrl` 类提供一组控制 `CToolTipCtrl` 对象的各种特性和工具提示窗口的成员函数。

可以通过调用[GetDelayTime](reference/ctooltipctrl-class.md#getdelaytime)和[SetDelayTime](reference/ctooltipctrl-class.md#setdelaytime)来设置和检索工具提示窗口的初始、弹出和 reshow 持续时间。

使用以下函数更改工具提示窗口的外观：

- [GetMargin](reference/ctooltipctrl-class.md#getmargin)和[SetMargin](reference/ctooltipctrl-class.md#setmargin)检索和设置工具提示边框与工具提示文本之间的宽度。

- [GetMaxTipWidth](reference/ctooltipctrl-class.md#getmaxtipwidth)和[SetMaxTipWidth](reference/ctooltipctrl-class.md#setmaxtipwidth)检索和设置工具提示窗口的最大宽度。

- [GetTipBkColor](reference/ctooltipctrl-class.md#gettipbkcolor)和[SetTipBkColor](reference/ctooltipctrl-class.md#settipbkcolor)检索和设置工具提示窗口的背景色。

- [GetTipTextColor](reference/ctooltipctrl-class.md#gettiptextcolor)和[SetTipTextColor](reference/ctooltipctrl-class.md#settiptextcolor)检索和设置工具提示窗口的文本颜色。

若要为工具提示控件通知重要消息，如 WM_LBUTTONXXX 消息，您必须将此消息传递给工具提示控件。 此中继的最佳方法是在所有者窗口的函数中调用[CToolTipCtrl：： RelayEvent](reference/ctooltipctrl-class.md#relayevent) `PreTranslateMessage` 。 以下示例演示了一种可能的方法（假定此工具提示控件名为 `m_ToolTip`）：

[!code-cpp[NVC_MFCControlLadenDialog#41](codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

若要立即删除 "工具提示" 窗口，请调用[Pop](reference/ctooltipctrl-class.md#pop)成员函数。

## <a name="see-also"></a>另请参阅

[使用 CToolTipCtrl](using-ctooltipctrl.md)<br/>
[控件](controls-mfc.md)
