---
title: 运行成员函数
ms.date: 11/04/2016
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
ms.openlocfilehash: 8271a10ad7439d2795dcc45d667b23b0932a0486
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271822"
---
# <a name="run-member-function"></a>运行成员函数

Framework 应用程序需要花大部分时间[运行](../mfc/reference/cwinapp-class.md#run)类的成员函数[CWinApp](../mfc/reference/cwinapp-class.md)。 初始化后`WinMain`调用`Run`来处理消息循环。

`Run` 依次切换程序消息循环，检查有可用消息的消息队列。 如果一条消息可用，`Run`调度的操作。 如果没有消息可用，这是通常为 true，`Run`调用`OnIdle`执行您或框架可能需要完成任何空闲时间处理。 如果没有要执行的消息和空闲处理，则应用程序将进行等待，直到发生某些情况。 当应用程序终止时，`Run`调用`ExitInstance`。 在图[OnIdle 成员函数](../mfc/onidle-member-function.md)消息循环中显示的操作序列。

消息调度取决于消息类型。 有关详细信息，请参阅[消息和框架中的命令](../mfc/messages-and-commands-in-the-framework.md)。

## <a name="see-also"></a>请参阅

[CWinApp:应用程序类](../mfc/cwinapp-the-application-class.md)
