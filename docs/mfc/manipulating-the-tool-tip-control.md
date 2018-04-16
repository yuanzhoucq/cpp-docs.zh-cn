---
title: "操作工具提示控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae30c39a26379aaa8a6f786b5fe2542abde2c2df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="manipulating-the-tool-tip-control"></a>操作工具提示控件
`CToolTipCtrl` 类提供一组控制 `CToolTipCtrl` 对象的各种特性和工具提示窗口的成员函数。  
  
 初始、 弹出和重新显示持续时间可以设置工具提示窗口，并将其调用与检索[GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime)和[SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime)。  
  
 使用以下函数更改工具提示窗口的外观：  
  
-   [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin)和[SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin)检索和设置提示文本的工具提示边框和工具之间的宽度。  
  
-   [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth)和[SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth)检索和设置的最大宽度的工具提示窗口。  
  
-   [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor)和[SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor)检索和设置的背景色的工具提示窗口。  
  
-   [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor)和[SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor)检索和设置的文本颜色的工具提示窗口。  
  
 为了使工具提示控件通知重要消息，如**WM_LBUTTONXXX**消息，必须将信息中继到你的工具提示控件。 此中继的最佳方法是调用[ctooltipctrl:: Relayevent](../mfc/reference/ctooltipctrl-class.md#relayevent)中`PreTranslateMessage`的所有者窗口的函数。 以下示例演示了一种可能的方法（假定此工具提示控件名为 `m_ToolTip`）：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]  
  
 若要立即移除工具提示窗口，调用[弹出](../mfc/reference/ctooltipctrl-class.md#pop)成员函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控件](../mfc/controls-mfc.md)

