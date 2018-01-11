---
title: "OnCmdMsg 处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OnCmdMsg
dev_langs: C++
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 173741ef73cd4bf6426787ef56e8334f504d7c0e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg 处理程序
为了完成命令路由，每个命令目标均将调用序列中下一命令目标的 `OnCmdMsg` 成员函数。 命令目标将使用 `OnCmdMsg` 确定它们是否可以处理命令并在无法处理命令时将其路由到其他命令目标。  
  
 每个命令目标类都可能重写 `OnCmdMsg` 成员函数。 通过重写，每个类会将命令路由到下一特定目标。 框架窗口，例如，始终将命令路由至其当前子窗口或视图中，表中所示[标准命令路由](../mfc/command-routing.md)。  
  
 `CCmdTarget` 的默认 `OnCmdMsg` 实现使用命令目标类的消息映射搜索收到的每条命令消息的处理程序函数 - 通过搜索标准消息的同一方式。 如果找到匹配项，则将调用找到的处理程序。 消息映射搜索中进行了说明[如何 Framework 搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)。  
  
## <a name="see-also"></a>请参阅  
 [框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)

