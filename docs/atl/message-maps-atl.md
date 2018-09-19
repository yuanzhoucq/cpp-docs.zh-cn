---
title: 消息映射 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b36ed5fc339fb49c7e58541465f2433804821fdb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762793"
---
# <a name="message-maps-atl"></a>消息映射 (ATL)

消息映射将与特定消息、 命令或通知关联的处理程序函数。 使用 ATL 的[消息映射宏](../atl/reference/message-map-macros-atl.md)，可以指定一个窗口消息映射。 中的窗口过程`CWindowImpl`， `CDialogImpl`，和`CContainedWindowT`窗口的消息定向到其消息映射。

[消息处理程序函数](../atl/message-handler-functions.md)接受类型的其他参数`BOOL&`。 此参数指示是否已处理一条消息，并且默认情况下设置为 TRUE。 然后，处理程序函数可以将参数设置为 FALSE 以指示它已不处理消息。 在这种情况下，ATL 将继续查找的消息映射中进一步的处理程序函数。 通过将此参数设置为 FALSE，您可以首先执行某些操作响应的消息，然后允许默认处理或另一个处理程序函数以完成处理消息。

## <a name="chained-message-maps"></a>链接的消息映射

ATL 还允许您向链消息映射，这会将定向到另一个类中定义的消息映射处理该消息。 例如，可以实现常见消息处理在单独的类以针对链接到该类的所有窗口提供统一的行为。 你可以链接到一个基类或您的类的数据成员。

ATL 还支持动态链接，可链接到另一个对象的消息映射在运行时。 若要实现动态链接，必须派生您的类从[CDynamicChain](../atl/reference/cdynamicchain-class.md)。 然后，声明[CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic)消息映射中的宏。 CHAIN_MSG_MAP_DYNAMIC 需要标识对象和消息映射到您要串联的唯一编号。 必须定义通过调用此唯一值`CDynamicChain::SetChainEntry`。

您可以链接到的任何类都声明消息映射中，提供的类派生[CMessageMap](../atl/reference/cmessagemap-class.md)。 `CMessageMap` 允许对象来公开其消息映射到其他对象。 请注意，`CWindowImpl`已从派生`CMessageMap`。

## <a name="alternate-message-maps"></a>替换消息映射

最后，ATL 支持备用消息映射，使用声明[ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map)宏。 由传递给 ALT_MSG_MAP 的唯一编号标识每个替换消息映射。 使用备用的消息映射，可以处理一个映射中的多个窗口的消息。 请注意，默认情况下，`CWindowImpl`不使用备用的消息映射。 若要添加此支持，请重写`WindowProc`中的方法您`CWindowImpl`的派生类，并调用`ProcessWindowMessage`使用消息映射标识符。

## <a name="see-also"></a>请参阅

[实现窗口](../atl/implementing-a-window.md)

