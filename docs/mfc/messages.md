---
title: 消息
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: 8e1bfd1baa8ffef76ba31912fc619c4217696683
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384122"
---
# <a name="messages"></a>消息

中的消息循环`Run`类的成员函数`CWinApp`检索生成的排队消息的各种事件。 例如，当用户单击鼠标，Windows 会发送多个与鼠标相关的消息，如 WM_LBUTTONDOWN 时按下鼠标左键和 WM_LBUTTONUP 释放鼠标按钮时。 应用程序消息循环的框架的实现会将消息调度到合适的窗口。

消息的重要类别中所述[消息类别](../mfc/message-categories.md)。

## <a name="see-also"></a>请参阅

[框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)
