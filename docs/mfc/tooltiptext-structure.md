---
title: "TOOLTIPTEXT 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TOOLTIPTEXT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "工具提示 [C++], 通知"
  - "TOOLTIPTEXT 结构"
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TOOLTIPTEXT 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在编写 [工具提示通知处理程序](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)，您需要使用 `TOOLTIPTEXT` 结构。  `TOOLTIPTEXT` 结构的成员为：  
  
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
 确定所需文本的工具。  可能需要此结构的成员是控件的命令 ID。  控件的命令 ID 在 `NMHDR` 结构的 `idFrom` 成员中，访问使用语法 `hdr.idFrom`。  讨论对 `NMHDR` 结构的成员请参阅 [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) 。  
  
 `lpszText`  
 接收工具文本的字符串地址。  
  
 `szText`  
 接收工具提示文本的缓存。  可以将文本复制到该缓冲区作为指定字符串的地址的应用程序。  
  
 `hinst`  
 包含作为工具提示文本中使用的字符串的实例处理程序。  如果 `lpszText` 为工具提示文本的地址，该成员为空。  
  
 当处理 `TTN_NEEDTEXT` 通知消息时，请指定以下方式之一中显示的字符串：  
  
-   将文本复制到 `szText` 成员指定的缓冲区。  
  
-   将包含缓冲区文本的地址复制到 `lpszText` 成员。  
  
-   复制字符串资源的标识符到 `lpszText` 成员，然后复制包含资源到 `hinst` 成员的实例处理程序。  
  
## 请参阅  
 [Windows 中不是从 CFrameWnd 派生的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)