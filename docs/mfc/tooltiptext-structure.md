---
title: TOOLTIPTEXT 结构
ms.date: 11/04/2016
f1_keywords:
- TOOLTIPTEXT
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
ms.openlocfilehash: 2eb899e66acbadbe45aae2c8adbb356bf4730191
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915246"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT 结构

编写[工具提示通知处理程序](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)时, 需要使用**TOOLTIPTEXT**结构。 **TOOLTIPTEXT**结构的成员包括:

```cpp
typedef struct {
    NMHDR     hdr;        // required for all WM_NOTIFY messages
    LPTSTR    lpszText;   // see below
    TCHAR     szText[80]; // buffer for tool tip text
    HINSTANCE hinst;      // see below
    UINT      uflags;     // flag indicating how to interpret the
                          // idFrom member of the NMHDR structure
                          // that is included in the structure
} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;
```

*hdr*<br/>
确定需要文本的工具。 您可能需要的此结构的唯一成员是控件的命令 ID。 控件的命令 ID 将位于**NMHDR**结构`hdr.idFrom`的*idFrom*成员中, 可通过语法访问。 有关**NMHDR**结构的成员的讨论, 请参阅[NMHDR](/windows/desktop/api/richedit/ns-richedit-nmhdr) 。

*lpszText*<br/>
接收工具文本的字符串的地址。

*szText*<br/>
接收工具提示文本的缓存区。 应用程序可将文本复制到此缓冲区以作为指定字符串地址的替代方法。

*hinst*<br/>
包含要用作工具提示文本的字符串的实例的句柄。 如果*lpszText*是工具提示文本的地址, 则此成员为 NULL。

当处理 `TTN_NEEDTEXT` 通知消息时，请指定要用以下方式之一显示的字符串：

- 将文本复制到*szText*成员指定的缓冲区。

- 将包含文本的缓冲区的地址复制到*lpszText*成员。

- 将字符串资源的标识符复制到*lpszText*成员, 并将包含该资源的实例的句柄复制到*hinst*成员。

## <a name="see-also"></a>请参阅

[Windows 中未从 CFrameWnd 派生的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
