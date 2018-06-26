---
title: 处理工具提示的 TTN_NEEDTEXT 通知 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TTN_NEEDTEXT
dev_langs:
- C++
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5879082ddc23630e5ee497d8abf6b65873a2b6d4
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931959"
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>处理工具提示的 TTN_NEEDTEXT 通知
作为的一部分[启用工具提示](../mfc/enabling-tool-tips.md)，你处理**TTN_NEEDTEXT**通过将以下条目添加到所有者窗口的消息映射的消息：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]  
  
 `memberFxn`  
 文本需要此按钮时调用的成员函数。  
  
 请注意，工具提示的 ID 始终为 0。  
  
 声明处理程序函数的类定义中，如下所示：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]  
  
 其中的斜体化的参数包括：  
  
 `id`  
 发送通知的控件的标识符。 未使用。 控件 id 取自**NMHDR**结构。  
  
 `pNMHDR`  
 指向的指针[NMTTDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760258)结构。 此结构还讨论了在中进一步[TOOLTIPTEXT 结构](../mfc/tooltiptext-structure.md)。  
  
 `pResult`  
 你可以设置指向结果代码的步骤，再返回。 **TTN_NEEDTEXT**处理程序可以忽略*pResult*参数。  
  
 例如，窗体视图通知处理程序：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]  
  
 调用`EnableToolTips`(摘自此片段`OnInitDialog`):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [Windows 中未从 CFrameWnd 派生的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

