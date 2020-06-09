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
ms.openlocfilehash: 5114fe53a5bac345eb6a55fb6c371f7bc1f698ef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624030"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg 处理程序

为了完成命令路由，每个命令目标均将调用序列中下一命令目标的 `OnCmdMsg` 成员函数。 命令目标将使用 `OnCmdMsg` 确定它们是否可以处理命令并在无法处理命令时将其路由到其他命令目标。

每个命令目标类都可能重写 `OnCmdMsg` 成员函数。 通过重写，每个类会将命令路由到下一特定目标。 例如，框架窗口始终将命令路由到其当前子窗口或视图，如表[标准命令路由](command-routing.md)中所示。

`CCmdTarget` 的默认 `OnCmdMsg` 实现使用命令目标类的消息映射搜索收到的每条命令消息的处理程序函数 - 通过搜索标准消息的同一方式。 如果找到匹配项，则将调用找到的处理程序。 [框架如何搜索消息](how-the-framework-searches-message-maps.md)映射中介绍了消息映射搜索。

## <a name="see-also"></a>另请参阅

[框架如何调用处理程序](how-the-framework-calls-a-handler.md)
