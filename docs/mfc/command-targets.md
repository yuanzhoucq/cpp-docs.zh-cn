---
title: 命令目标
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: 59ba197174e95e42cd237c875f39f07801cb3dbe
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619316"
---
# <a name="command-targets"></a>命令目标

[框架中](user-interface-objects-and-command-ids.md)的图形命令显示了用户界面对象（如菜单项）与框架调用的处理程序函数之间的连接，以在单击对象时执行生成的命令。

Windows 直接将不是命令消息的消息发送到某个窗口，随后将调用该窗口的针对该消息的处理程序。 但是，框架会将命令传送到很多候选对象（称为“命令目标”），其中一个对象通常会调用命令的处理程序。 处理程序函数对于命令和标准 Windows 消息的工作方式相同，但调用它们的机制不同，如[框架如何调用处理程序](how-the-framework-calls-a-handler.md)中所述。

## <a name="see-also"></a>另请参阅

[框架中的消息和命令](messages-and-commands-in-the-framework.md)
