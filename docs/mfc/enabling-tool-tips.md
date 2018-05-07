---
title: 启用工具提示 |Microsoft 文档
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
ms.openlocfilehash: 598583360eca2a65a5352fc9d284d8d359ac021c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="enabling-tool-tips"></a>启用工具提示
您可以为窗口的子控件（如窗体视图或对话框上的控件）启用工具提示支持。  
  
### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>为窗口的子控件启用工具提示  
  
1.  为要为其提供要提供工具提示的窗口调用 `EnableToolTips`。  
  
2.  为在每个控件提供字符串你[TTN_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)处理程序。 处理程序位于包含子控件（例如，窗体视图类）的窗口的消息映射中。 此处理程序应调用的函数的标识控件并设置**pszText**指定使用工具提示控件的文本。  
  
## <a name="see-also"></a>请参阅  
 [Windows 中未从 CFrameWnd 派生的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

