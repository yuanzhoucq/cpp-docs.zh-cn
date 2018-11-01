---
title: 非命令消息如何到达其处理程序
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: f64eb97315b41a314c791e1a4c5bc7721b329fca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545452"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>非命令消息如何到达其处理程序

与命令不同，标准 Windows 消息不会路由至命令链的目标，但通常处理通过 Windows 将消息发送到的窗口。 窗口可能是主框架窗口、 的 MDI 子窗口、 标准控件、 对话框、 视图或某种其他类型的子窗口。

在运行时，每个 Windows 窗口附加到窗口对象 (直接或间接派生自`CWnd`) 具有其自身相关联的消息映射和处理程序函数。 框架使用消息映射 — 与命令，将传入消息映射到处理程序。

## <a name="see-also"></a>请参阅

[框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)

