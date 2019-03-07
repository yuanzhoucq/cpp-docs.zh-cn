---
title: OnCmdMsg 处理程序
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 6ed2e4c09e2fe413d29ad9953dbb8a03c106e86c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274591"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg 处理程序

为了完成命令路由，每个命令目标均将调用序列中下一命令目标的 `OnCmdMsg` 成员函数。 命令目标将使用 `OnCmdMsg` 确定它们是否可以处理命令并在无法处理命令时将其路由到其他命令目标。

每个命令目标类都可能重写 `OnCmdMsg` 成员函数。 通过重写，每个类会将命令路由到下一特定目标。 框架窗口，例如，始终将命令路由至其当前子窗口或视图中，表中所示[标准命令传送](../mfc/command-routing.md)。


  `CCmdTarget` 的默认 `OnCmdMsg` 实现使用命令目标类的消息映射搜索收到的每条命令消息的处理程序函数 - 通过搜索标准消息的同一方式。 如果找到匹配项，则将调用找到的处理程序。 消息映射搜索所述[如何 Framework 搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)。

## <a name="see-also"></a>请参阅

[框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)
