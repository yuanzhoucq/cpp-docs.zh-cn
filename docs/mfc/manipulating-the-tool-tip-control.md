---
title: 操作工具提示控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91e2e247acb85188c1280713e9e5ad8ef8f19448
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929823"
---
# <a name="manipulating-the-tool-tip-control"></a>操作工具提示控件
`CToolTipCtrl` 类提供一组控制 `CToolTipCtrl` 对象的各种特性和工具提示窗口的成员函数。  
  
 初始、 弹出和重新显示持续时间可以设置工具提示窗口，并将其调用与检索[GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime)和[SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime)。  
  
 使用以下函数更改工具提示窗口的外观：  
  
-   [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin)和[SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin)检索和设置提示文本的工具提示边框和工具之间的宽度。  
  
-   [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth)和[SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth)检索和设置的最大宽度的工具提示窗口。  
  
-   [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor)和[SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor)检索和设置的背景色的工具提示窗口。  
  
-   [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor)和[SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor)检索和设置的文本颜色的工具提示窗口。  
  
 为了使工具提示控件通知重要消息，例如 WM_LBUTTONXXX 消息，必须向工具提示控件中继消息。 此中继的最佳方法是调用[ctooltipctrl:: Relayevent](../mfc/reference/ctooltipctrl-class.md#relayevent)中`PreTranslateMessage`的所有者窗口的函数。 以下示例演示了一种可能的方法（假定此工具提示控件名为 `m_ToolTip`）：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]  
  
 若要立即移除工具提示窗口，调用[弹出](../mfc/reference/ctooltipctrl-class.md#pop)成员函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控件](../mfc/controls-mfc.md)

