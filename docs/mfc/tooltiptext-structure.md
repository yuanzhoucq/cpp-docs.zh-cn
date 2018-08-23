---
title: TOOLTIPTEXT 结构 |Microsoft 文档
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
ms.openlocfilehash: 8cae7efbee59b24ff34518b62ff212d436973053
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953927"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT 结构
在编写你[工具提示通知处理程序](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)，你需要使用**TOOLTIPTEXT**结构。 成员**TOOLTIPTEXT**结构不是：  
  
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
 确定需要文本的工具。 您可能需要的此结构的唯一成员是控件的命令 ID。 控件的命令 ID 将在*idFrom*的成员**NMHDR**结构，可通过语法访问`hdr.idFrom`。 请参阅[NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514)有关的成员的讨论**NMHDR**结构。  
  
 *lpszText*  
 接收工具文本的字符串的地址。  
  
 *szText*  
 接收工具提示文本的缓存区。 应用程序可将文本复制到此缓冲区以作为指定字符串地址的替代方法。  
  
 *hinst*  
 包含要用作工具提示文本的字符串的实例的句柄。 如果*lpszText*是的地址的工具提示文本，此成员为 NULL。  
  
 当处理 `TTN_NEEDTEXT` 通知消息时，请指定要用以下方式之一显示的字符串：  
  
-   将文本复制到指定的缓冲区*szText*成员。  
  
-   包含要进行的文本的缓冲区的地址复制*lpszText*成员。  
  
-   将复制到字符串资源的标识符*lpszText*成员，并复制包含资源的实例的句柄*hinst*成员。  
  
## <a name="see-also"></a>请参阅  
 [Windows 中未从 CFrameWnd 派生的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

