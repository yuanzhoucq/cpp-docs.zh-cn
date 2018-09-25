---
title: 启用工具提示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 968d31b49c6d2b2fe5a5f69e04f58f17de8df5a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440480"
---
# <a name="enabling-tool-tips"></a>启用工具提示

您可以为窗口的子控件（如窗体视图或对话框上的控件）启用工具提示支持。

### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>为窗口的子控件启用工具提示

1. 为要为其提供要提供工具提示的窗口调用 `EnableToolTips`。

1. 中每个控件提供一个字符串，你[TTN_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)处理程序。 处理程序位于包含子控件（例如，窗体视图类）的窗口的消息映射中。 此处理程序应调用的函数的标识控件并设置**pszText**指定使用的工具提示控件的文本。

## <a name="see-also"></a>请参阅

[Windows 中未从 CFrameWnd 派生的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

