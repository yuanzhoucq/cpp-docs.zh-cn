---
title: 处理工具提示的 TTN_NEEDTEXT 通知
ms.date: 11/04/2016
f1_keywords:
- TTN_NEEDTEXT
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
ms.openlocfilehash: 97db98322cd7c0d14e46f54a055bbc646c90d785
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240382"
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>处理工具提示的 TTN_NEEDTEXT 通知

作为的一部分[启用工具提示](../mfc/enabling-tool-tips.md)，则处理**TTN_NEEDTEXT**通过将以下条目添加到所有者窗口的消息映射的消息：

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
文本所需的此按钮时要调用的成员函数。

请注意，工具提示的 ID 始终为 0。

声明类定义中的处理程序函数，如下所示：

[!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

其中的斜体的参数包括：

*id*<br/>
向你发送通知的控件标识符。 未使用。 控件 id 取自**NMHDR**结构。

*pNMHDR*<br/>
一个指向[NMTTDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagnmttdispinfoa)结构。 此外讨论了此结构中进一步[TOOLTIPTEXT 结构](../mfc/tooltiptext-structure.md)。

*pResult*<br/>
您可以设置指向结果代码的步骤，再返回。 **TTN_NEEDTEXT**处理程序可以忽略*pResult*参数。

例如，窗体视图通知处理程序：

[!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

调用`EnableToolTips`(来自此片段`OnInitDialog`):

[!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>请参阅

[Windows 中未从 CFrameWnd 派生的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
