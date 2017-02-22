---
title: "Message Map Macros (ATL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# Message Map Macros (ATL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些宏定义消息映射和项。  
  
|||  
|-|-|  
|[ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md)|标记替换消息映射的开头。|  
|[BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)|标记默认的消息映射的开头。|  
|[CHAIN\_MSG\_MAP\_ALT](../Topic/CHAIN_MSG_MAP_ALT.md)|对备用消息的链接到基类映射。|  
|[CHAIN\_MSG\_MAP\_ALT\_MEMBER](../Topic/CHAIN_MSG_MAP_ALT_MEMBER.md)|对备用消息的链接到选件类的数据成员映射。|  
|[CHAIN\_MSG\_MAP](../Topic/CHAIN_MSG_MAP.md)|对默认消息的链接到基类映射。|  
|[CHAIN\_MSG\_MAP\_DYNAMIC](../Topic/CHAIN_MSG_MAP_DYNAMIC.md)|对消息的链接到另一选件类映射在运行时。|  
|[CHAIN\_MSG\_MAP\_MEMBER](../Topic/CHAIN_MSG_MAP_MEMBER.md)|对默认消息的链接到选件类的数据成员映射。|  
|[COMMAND\_CODE\_HANDLER](../Topic/COMMAND_CODE_HANDLER.md)|映射到 **WM\_COMMAND** 消息给处理程序函数，根据通知代码。|  
|[COMMAND\_HANDLER](../Topic/COMMAND_HANDLER.md)|映射到 **WM\_COMMAND** 消息给处理程序函数，根据通知代码和菜单项、控件或快捷键的标识符。|  
|[COMMAND\_ID\_HANDLER](../Topic/COMMAND_ID_HANDLER.md)|映射到 **WM\_COMMAND** 消息给处理程序函数，具体取决于菜单项、控件或快捷键的标识符。|  
|[COMMAND\_RANGE\_CODE\_HANDLER](../Topic/COMMAND_RANGE_CODE_HANDLER.md)|映射到 **WM\_COMMAND** 消息给处理程序函数，根据通知代码和控件标识符的一个连续范围。|  
|[COMMAND\_RANGE\_HANDLER](../Topic/COMMAND_RANGE_HANDLER.md)|映射到 **WM\_COMMAND** 消息给处理程序函数，根据控件标识符的一个连续范围。|  
|[DECLARE\_EMPTY\_MSG\_MAP](../Topic/DECLARE_EMPTY_MSG_MAP.md)|实现空消息映射。|  
|[DEFAULT\_REFLECTION\_HANDLER](../Topic/DEFAULT_REFLECTION_HANDLER.md)|对于不否则将处理的反射消息提供了默认的处理程序。|  
|[END\_MSG\_MAP](../Topic/END_MSG_MAP.md)|标记消息映射的结尾。|  
|[FORWARD\_NOTIFICATIONS](../Topic/FORWARD_NOTIFICATIONS.md)|向前通知消息到父窗口。|  
|[MESSAGE\_HANDLER](../Topic/MESSAGE_HANDLER.md)|映射到Windows消息处理程序功能。|  
|[MESSAGE\_RANGE\_HANDLER](../Topic/MESSAGE_RANGE_HANDLER.md)|映射Windows消息的一个连续范围给处理程序函数。|  
|[NOTIFY\_CODE\_HANDLER](../Topic/NOTIFY_CODE_HANDLER.md)|映射到 **WM\_NOTIFY** 消息给处理程序函数，根据通知代码。|  
|[NOTIFY\_HANDLER](../Topic/NOTIFY_HANDLER.md)|映射到 **WM\_NOTIFY** 消息给处理程序函数，根据通知代码和控件标识符。|  
|[NOTIFY\_ID\_HANDLER](../Topic/NOTIFY_ID_HANDLER.md)|映射到 **WM\_NOTIFY** 消息给处理程序函数，根据控件标识符。|  
|[NOTIFY\_RANGE\_CODE\_HANDLER](../Topic/NOTIFY_RANGE_CODE_HANDLER.md)|映射到 **WM\_NOTIFY** 消息给处理程序函数，根据通知代码和控件标识符的一个连续范围。|  
|[NOTIFY\_RANGE\_HANDLER](../Topic/NOTIFY_RANGE_HANDLER.md)|映射到 **WM\_NOTIFY** 消息给处理程序函数，根据控件标识符的一个连续范围。|  
|[REFLECT\_NOTIFICATIONS](../Topic/REFLECT_NOTIFICATIONS.md)|反映通知消息发送回它们的窗口。|  
|[REFLECTED\_COMMAND\_CODE\_HANDLER](../Topic/REFLECTED_COMMAND_CODE_HANDLER.md)|映射反射的 **WM\_COMMAND** 消息给处理程序函数，根据通知代码。|  
|[REFLECTED\_COMMAND\_HANDLER](../Topic/REFLECTED_COMMAND_HANDLER.md)|映射反射的 **WM\_COMMAND** 消息给处理程序函数，根据通知代码和菜单项、控件或快捷键的标识符。|  
|[REFLECTED\_COMMAND\_ID\_HANDLER](../Topic/REFLECTED_COMMAND_ID_HANDLER.md)|映射反射的 **WM\_COMMAND** 消息给处理程序函数，具体取决于菜单项、控件或快捷键的标识符。|  
|[REFLECTED\_COMMAND\_RANGE\_CODE\_HANDLER](../Topic/REFLECTED_COMMAND_RANGE_CODE_HANDLER.md)|映射反射的 **WM\_COMMAND** 消息给处理程序函数，根据通知代码和控件标识符的一个连续范围。|  
|[REFLECTED\_COMMAND\_RANGE\_HANDLER](../Topic/REFLECTED_COMMAND_RANGE_HANDLER.md)|映射反射的 **WM\_COMMAND** 消息给处理程序函数，根据控件标识符的一个连续范围。|  
|[REFLECTED\_NOTIFY\_CODE\_HANDLER](../Topic/REFLECTED_NOTIFY_CODE_HANDLER.md)|映射反射的 **WM\_NOTIFY** 消息给处理程序函数，根据通知代码。|  
|[REFLECTED\_NOTIFY\_HANDLER](../Topic/REFLECTED_NOTIFY_HANDLER.md)|映射反射的 **WM\_NOTIFY** 消息给处理程序函数，根据通知代码和控件标识符。|  
|[REFLECTED\_NOTIFY\_ID\_HANDLER](../Topic/REFLECTED_NOTIFY_ID_HANDLER.md)|映射反射的 **WM\_NOTIFY** 消息给处理程序函数，根据控件标识符。|  
|[REFLECTED\_NOTIFY\_RANGE\_CODE\_HANDLER](../Topic/REFLECTED_NOTIFY_RANGE_CODE_HANDLER.md)|映射反射的 **WM\_NOTIFY** 消息给处理程序函数，根据通知代码和控件标识符的一个连续范围。|  
|[REFLECTED\_NOTIFY\_RANGE\_HANDLER](../Topic/REFLECTED_NOTIFY_RANGE_HANDLER.md)|映射反射的 **WM\_NOTIFY** 消息给处理程序函数，根据控件标识符的一个连续范围。|  
  
## 请参阅  
 [Macros](../../atl/reference/atl-macros.md)