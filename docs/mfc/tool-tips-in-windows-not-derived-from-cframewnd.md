---
title: 未从 CFrameWnd 派生的 Windows 中的工具提示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea6f39f8c1478715ecc656ca84c1d6b24b7c03b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445511"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Windows 中不是从 CFrameWnd 派生的工具提示

本文章系列介绍了在不派生自的窗口中所包含控件启用工具提示[CFrameWnd](../mfc/reference/cframewnd-class.md)。 文章[工具栏工具提示](../mfc/toolbar-tool-tips.md)中的控件提供工具提示信息`CFrameWnd`。

在本文章系列中的主题包括：

- [启用工具提示](../mfc/enabling-tool-tips.md)

- [处理工具提示的 TTN_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [TOOLTIPTEXT 结构](../mfc/tooltiptext-structure.md)

为按钮自动显示工具提示，并包含在父窗口中其他控件派生自`CFrameWnd`。 这是因为`CFrameWnd`具有默认处理程序[TTN_GETDISPINFO](/windows/desktop/Controls/ttn-getdispinfo)通知，处理**TTN_NEEDTEXT**通知从工具提示与控件关联的控件。

但是，此默认处理程序未调用何时**TTN_NEEDTEXT**从工具提示控件与不是一个窗口中的控件相关联发送通知`CFrameWnd`，如对话框或窗体视图上的控件。 因此，有必要为您提供的处理程序函数**TTN_NEEDTEXT**通知消息中，以便显示子控件的工具提示。

对由 windows 提供的默认工具提示[CWnd::EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips)不具有与其关联的文本。 若要检索文本的工具提示显示，请**TTN_NEEDTEXT**恰好在显示工具提示窗口之前，会向工具提示控件的父窗口发送通知。 如果没有将某些值分配给此消息处理程序*pszText*的成员**TOOLTIPTEXT**结构，将有没有为工具提示显示的文本。

## <a name="see-also"></a>请参阅

[工具提示](../mfc/tool-tips.md)

