---
title: "消息映射宏 (MFC) | Microsoft Docs"
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
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "划分 Windows 消息"
  - "消息映射宏"
  - "消息映射范围"
  - "消息映射宏"
  - "消息映射 [C++], 声明和划分"
  - "消息映射 [C++], 宏"
  - "范围, 消息映射"
  - "Windows 消息 [C++], 声明"
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 消息映射宏 (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为了支持 MFC 提供消息映射，下面的宏：  
  
### 声明将宏和消息映射  
  
|||  
|-|-|  
|[DECLARE\_MESSAGE\_MAP](../Topic/DECLARE_MESSAGE_MAP.md)|消息声明映射在类消息映射到函数 \(必须在类中声明\)。|  
|[BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md)|启动消息映射的定义 \(必须在类中实现。\)|  
|[END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md)|结束消息映射的定义 \(必须在类中实现。\)|  
  
### 消息映射宏  
  
|||  
|-|-|  
|[ON\_COMMAND](../Topic/ON_COMMAND.md)|指示函数将指定的命令处理消息。|  
|[ON\_CONTROL](../Topic/ON_CONTROL.md)|指示函数将处理指定的控件通知消息。|  
|[ON\_MESSAGE](../Topic/ON_MESSAGE.md)|指示函数将处理的用户定义消息。|  
|[ON\_OLECMD](../Topic/ON_OLECMD.md)|指示函数将从处理 DocObject 或其容器的菜单命令。|  
|[ON\_REGISTERED\_MESSAGE](../Topic/ON_REGISTERED_MESSAGE.md)|指示函数将处理的用户定义消息。|  
|[ON\_REGISTERED\_THREAD\_MESSAGE](../Topic/ON_REGISTERED_THREAD_MESSAGE.md)|指示函数将处理已注册的用户定义消息，则您有一个 `CWinThread` 类。|  
|[ON\_THREAD\_MESSAGE](../Topic/ON_THREAD_MESSAGE.md)|指示函数将处理已注册的用户定义消息，则您有一个 `CWinThread` 类。|  
|[ON\_UPDATE\_COMMAND\_UI](../Topic/ON_UPDATE_COMMAND_UI.md)|指示处理函数将指定的用户界面更新命令消息。|  
  
### 消息将范围映射宏  
  
|||  
|-|-|  
|[ON\_COMMAND\_RANGE](../Topic/ON_COMMAND_RANGE.md)|指示哪一个函数来处理前面两参数命令 ID 指定的范围传递给宏。|  
|[ON\_UPDATE\_COMMAND\_UI\_RANGE](../Topic/ON_UPDATE_COMMAND_UI_RANGE.md)|指示哪一个函数来处理前面两参数命令 ID 指定的范围传递给宏。|  
|[ON\_CONTROL\_RANGE](../Topic/ON_CONTROL_RANGE.md)|指示函数将从处理在第二个和第三个参数指定控件 ID 范围的通知给宏。  第一个参数是一控件通知消息，例如 **BN\_CLICKED**。|  
  
 有关消息的更多信息，将声明和消息映射宏和消息映射宏，请参见 [消息映射](../../mfc/reference/message-maps-mfc.md) 和 [和消息映射处理主题](../../mfc/message-handling-and-mapping.md)。  有关消息映射范围的更多信息，请参见 [消息映射范围的处理程序](../../mfc/handlers-for-message-map-ranges.md)。  
  
## 请参阅  
 [消息映射](../../mfc/reference/message-maps-mfc.md)