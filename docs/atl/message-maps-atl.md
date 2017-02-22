---
title: "Message Maps (ATL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 消息处理程序"
  - "message maps, ATL"
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Message Maps (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

消息映射将处理程序函数与特定消息、命令或通知。  通过使用ATL的 [消息映射宏](../atl/reference/message-map-macros-atl.md)，可以为windows指定消息映射。  在 `CWindowImpl`、 `CDialogImpl`和 `CContainedWindowT` 的窗口过程处理windows消息到其消息映射。  
  
 [消息处理函数](../atl/message-handler-functions.md) 接受类型 `BOOL&`的其他参数。  此参数指示消息是否处理，默认情况下，它设置为 `TRUE`。  处理程序函数可以将参数设置为 `FALSE` 指示尚未处理消息。  在这种情况下，ATL将继续查找一个处理程序功能进一步在消息映射。  通过设置为 `FALSE`的此参数，您可以先执行某些操作以响应消息然后允许默认处理或另一个处理程序功能。处理消息的完成。  
  
## 链接的消息映射  
 ATL还允许您将消息映射，处理消息处理对另一选件类定义的消息映射。  例如，可以实现处理在单独的选件类的常用消息用于绑定的所有窗口提供统一行为到该选件类。  您可以绑定到基类或对选件类的数据成员。  
  
 ATL还支持动态绑定，使您可以绑定到另一个对象的消息映射在运行时。  若要实现动态绑定，必须从 [CDynamicChain](../atl/reference/cdynamicchain-class.md)派生您的选件类。  然后声明中的消息映射的 [CHAIN\_MSG\_MAP\_DYNAMIC](../Topic/CHAIN_MSG_MAP_DYNAMIC.md) 宏。  `CHAIN_MSG_MAP_DYNAMIC` 需要标识对象和消息映射要绑定的一个唯一编号）。  必须通过调用定义此唯一值。`CDynamicChain::SetChainEntry`。  
  
 您可以绑定到声明消息映射中的任何选件类，在中，假定选件类从 [CMessageMap](../atl/reference/cmessagemap-class.md)派生。  `CMessageMap` 允许对象显示其消息映射在其他对象。  请注意 `CWindowImpl` 从 `CMessageMap`已派生。  
  
## 替换消息映射  
 最后，ATL支持替换消息映射，声明了 [ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md) 宏。  每个替换消息映射由一个唯一编号标识，传递给 `ALT_MSG_MAP`。  使用替换消息映射，可以处理多个窗口消息。一的映射。  请注意，默认情况下，`CWindowImpl` 不使用替换消息映射。  为此，请重写在您的 `CWindowImpl`的 `WindowProc` 方法的派生类并调用与消息映射的标识符 `ProcessWindowMessage`。  
  
## 请参阅  
 [Implementing a Window](../atl/implementing-a-window.md)