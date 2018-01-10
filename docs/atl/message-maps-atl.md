---
title: "消息映射 (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e708fea75c594c7bb9504515c80222ad901c335
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="message-maps-atl"></a>消息映射 (ATL)
消息映射将与特定的消息、 命令或通知关联的处理程序函数。 使用 ATL 的[消息映射宏](../atl/reference/message-map-macros-atl.md)，你可以指定一个窗口消息映射。 中的窗口过程`CWindowImpl`， `CDialogImpl`，和`CContainedWindowT`窗口将消息定向到其消息映射。  
  
 [消息处理程序函数](../atl/message-handler-functions.md)接受其他参数的类型`BOOL&`。 此参数用于指示是否已处理消息，并且设置为`TRUE`默认情况下。 处理程序函数然后可以将参数设置为`FALSE`以指示它已不处理消息。 在这种情况下，ATL 将继续查找的消息映射中进一步的处理程序函数。 通过此参数设置为`FALSE`，你可以首先执行某些操作，以响应的消息，然后允许默认处理或另一个处理程序函数来完成消息的处理。  
  
## <a name="chained-message-maps"></a>链接的消息映射  
 ATL 还允许你为链消息映射，以便将定向到另一个类中定义的消息映射处理的消息。 例如，你可以实现常见消息处理在单独的类以针对链接到该类的所有窗口提供统一的行为。 你可以链接到的基类或到您的类的数据成员。  
  
 ATL 还支持动态链接，这使你链接到另一个对象的消息映射在运行时。 若要实现动态链接，必须派生您的类从[CDynamicChain](../atl/reference/cdynamicchain-class.md)。 然后，声明[CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic)消息映射中的宏。 `CHAIN_MSG_MAP_DYNAMIC`需要一个标识该对象，并且你将链接的消息映射的唯一数字。 你必须定义通过调用此唯一值`CDynamicChain::SetChainEntry`。  
  
 您可以链接到的任何类都声明一个消息映射，提供的类派生自[CMessageMap](../atl/reference/cmessagemap-class.md)。 `CMessageMap`允许该对象来公开其消息映射到其他对象。 请注意，`CWindowImpl`已派生自`CMessageMap`。  
  
## <a name="alternate-message-maps"></a>替换消息映射  
 最后，ATL 支持备用消息映射，使用声明[ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map)宏。 每个替换消息映射标识唯一的编号，传递给`ALT_MSG_MAP`。 使用备用消息映射，你可以处理的消息的一个映射中的多个窗口。 请注意，默认情况下，`CWindowImpl`不使用备用的消息映射。 若要添加此支持，请重写`WindowProc`方法在你`CWindowImpl`-派生的类和调用`ProcessWindowMessage`与消息映射标识符。  
  
## <a name="see-also"></a>请参阅  
 [实现窗口](../atl/implementing-a-window.md)

