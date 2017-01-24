---
title: "启用工具提示 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "启用工具提示"
  - "初始化工具提示"
  - "工具提示 [C++], 启用"
  - "工具提示 [C++], 初始化"
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 启用工具提示
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以启用窗口的子控件的工具提示 \(如支持在窗体视图或对话框的控件\)。  
  
### 支持针对窗口的子控件的工具提示  
  
1.  调用要提供工具提示窗口的 `EnableToolTips`。  
  
2.  可在 [TTN\_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md) 处理程序的每个控件提供字符串。  处理程序为例如包含子控件的 Windows 消息映射 \(，窗体视图类\)。  该处理程序应调用标识控件并将 **pszText** 指定工具提示控件使用文本的函数。  
  
## 请参阅  
 [Windows 中不是从 CFrameWnd 派生的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)