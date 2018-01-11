---
title: "TOOLTIPTEXT 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TOOLTIPTEXT
dev_langs: C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: becbdcfcc6dbd26ae3095de098d12dbc078530cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT 结构
在编写你[工具提示通知处理程序](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)，你需要使用`TOOLTIPTEXT`结构。 成员`TOOLTIPTEXT`结构不是：  
  
 `typedef struct {`  
  
 `NMHDR     hdr;        // required for all WM_NOTIFY messages`  
  
 `LPTSTR    lpszText;   // see below`  
  
 `TCHAR     szText[80]; // buffer for tool tip text`  
  
 `HINSTANCE hinst;      // see below`  
  
 `UINT      uflags;     // flag indicating how to interpret the`  
  
 `// idFrom member of the NMHDR structure`  
  
 `// that is included in the structure`  
  
 `} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;`  
  
 `hdr`  
 确定需要文本的工具。 您可能需要的此结构的唯一成员是控件的命令 ID。 控件的命令 ID 将在 `idFrom` 结构的 `NMHDR` 成员中，可使用语法 `hdr.idFrom` 访问。 请参阅[NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514)有关的成员的讨论`NMHDR`结构。  
  
 `lpszText`  
 接收工具文本的字符串的地址。  
  
 `szText`  
 接收工具提示文本的缓存区。 应用程序可将文本复制到此缓冲区以作为指定字符串地址的替代方法。  
  
 `hinst`  
 包含要用作工具提示文本的字符串的实例的句柄。 如果 `lpszText` 为工具提示文本的地址，此成员为 NULL。  
  
 当处理 `TTN_NEEDTEXT` 通知消息时，请指定要用以下方式之一显示的字符串：  
  
-   将文本复制到 `szText` 成员中指定的缓冲区。  
  
-   将包含文本的缓冲区的地址复制到 `lpszText` 成员。  
  
-   将字符串资源的标识符复制到 `lpszText` 成员，然后将包含资源的实例的句柄复制到 `hinst` 成员。  
  
## <a name="see-also"></a>请参阅  
 [Windows 中未从 CFrameWnd 派生的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

