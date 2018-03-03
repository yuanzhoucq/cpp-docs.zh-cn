---
title: "命令目标 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb8d2bff69e95a089827c85ade6dc4bcd67eb7ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="command-targets"></a>命令目标
图[框架中的命令](../mfc/user-interface-objects-and-command-ids.md)显示一个用户界面对象，如菜单项，并与框架调用生成的命令在单击该对象时执行的处理程序函数之间的连接。  
  
 Windows 直接将不是命令消息的消息发送到某个窗口，随后将调用该窗口的针对该消息的处理程序。 但是，框架会将命令传送到很多候选对象（称为“命令目标”），其中一个对象通常会调用命令的处理程序。 处理程序函数工作相同的方式针对命令和标准 Windows 消息，但调用它们所依据的机制不同中, 所述[框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)。  
  
## <a name="see-also"></a>请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)

