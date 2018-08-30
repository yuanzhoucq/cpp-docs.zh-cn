---
title: TOOLTIPTEXT 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TOOLTIPTEXT
dev_langs:
- C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f65b94294b3b3d55f9839dffa99a18be61c5639
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195979"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT 结构
在编写你[工具提示通知处理程序](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)，你需要使用**TOOLTIPTEXT**结构。 成员**TOOLTIPTEXT**结构是：  
  
 `typedef struct {`  
  
 `NMHDR     hdr;        // required for all WM_NOTIFY messages`  
  
 `LPTSTR    lpszText;   // see below`  
  
 `TCHAR     szText[80]; // buffer for tool tip text`  
  
 `HINSTANCE hinst;      // see below`  
  
 `UINT      uflags;     // flag indicating how to interpret the`  
  
 `// idFrom member of the NMHDR structure`  
  
 `// that is included in the structure`  
  
 `} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;`  
  
 *hdr*  
 确定需要文本的工具。 您可能需要的此结构的唯一成员是控件的命令 ID。 控件的命令 ID 将在*idFrom*的成员**NMHDR**结构，可通过语法访问`hdr.idFrom`。 请参阅[NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr)有关的成员的讨论**NMHDR**结构。  
  
 *lpszText*  
 接收工具文本的字符串的地址。  
  
 *szText*  
 接收工具提示文本的缓存区。 应用程序可将文本复制到此缓冲区以作为指定字符串地址的替代方法。  
  
 *hinst*  
 包含要用作工具提示文本的字符串的实例的句柄。 如果*lpszText*是地址的工具提示文本，此成员为 NULL。  
  
 当处理 `TTN_NEEDTEXT` 通知消息时，请指定要用以下方式之一显示的字符串：  
  
-   将文本复制到指定的缓冲区*szText*成员。  
  
-   将复制包含到文本的缓冲区的地址*lpszText*成员。  
  
-   将复制到字符串资源的标识符*lpszText*成员，并复制包含对资源的实例的句柄*hinst*成员。  
  
## <a name="see-also"></a>请参阅  
 [Windows 中未从 CFrameWnd 派生的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

