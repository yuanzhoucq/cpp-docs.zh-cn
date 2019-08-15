---
title: Windows 中不是从 CFrameWnd 派生的工具提示
ms.date: 11/04/2016
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
ms.openlocfilehash: 1f68fb62335219ea498163e6124c8e91e49f2938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511033"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Windows 中不是从 CFrameWnd 派生的工具提示

本文介绍如何为不是从[CFrameWnd](../mfc/reference/cframewnd-class.md)派生的窗口中包含的控件启用工具提示。 文章[工具栏工具提示](../mfc/toolbar-tool-tips.md)提供了有关中`CFrameWnd`控件的工具提示的信息。

本文系列中涵盖的主题包括:

- [启用工具提示](../mfc/enabling-tool-tips.md)

- [处理工具提示的 TTN_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [TOOLTIPTEXT 结构](../mfc/tooltiptext-structure.md)

对于从派生的`CFrameWnd`父窗口中包含的按钮和其他控件, 将自动显示工具提示。 这是因为`CFrameWnd` , 有[TTN_GETDISPINFO](/windows/win32/Controls/ttn-getdispinfo)通知的默认处理程序, 该处理程序处理与控件关联的工具提示控件中的**TTN_NEEDTEXT**通知。

但是, 当从与不是的`CFrameWnd`窗口 (例如, 对话框中的控件或窗体视图的控件) 关联的工具提示控件发送**TTN_NEEDTEXT**通知时, 不会调用此默认处理程序。 因此, 需要为**TTN_NEEDTEXT**通知消息提供处理程序函数, 以便显示子控件的工具提示。

为 windows 通过[CWnd:: EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips)提供的默认工具提示没有关联的文本。 若要检索要显示的工具提示的文本, 则在显示 "工具提示" 窗口之前, 会将**TTN_NEEDTEXT**通知发送到工具提示控件的父窗口。 如果此消息没有处理程序来向**TOOLTIPTEXT**结构的*pszText*成员分配某些值, 则工具提示将不会显示任何文本。

## <a name="see-also"></a>请参阅

[工具提示](../mfc/tool-tips.md)
