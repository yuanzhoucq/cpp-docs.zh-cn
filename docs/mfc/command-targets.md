---
title: 命令目标
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: ed3d6a68967dc7f4244f887ae34760fdb99fa7f5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274435"
---
# <a name="command-targets"></a>命令目标

图[框架中的命令](../mfc/user-interface-objects-and-command-ids.md)显示用户界面对象，如菜单项，并与框架调用时单击对象后执行生成的命令的处理程序函数之间的连接。

Windows 直接将不是命令消息的消息发送到某个窗口，随后将调用该窗口的针对该消息的处理程序。 但是，框架会将命令传送到很多候选对象（称为“命令目标”），其中一个对象通常会调用命令的处理程序。 处理程序函数的工作方式类似的命令和标准 Windows 消息，但调用它们所依据的机制不同，如中所述[框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)。

## <a name="see-also"></a>请参阅

[框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)
