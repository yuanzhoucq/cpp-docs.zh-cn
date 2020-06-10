---
title: 非命令消息如何到达其处理程序
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: c7b2bf819c5305da4039fae172578298d3b4e609
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618512"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>非命令消息如何到达其处理程序

与命令不同，标准 Windows 消息不通过命令目标链进行路由，但通常由 Windows 发送消息的窗口处理。 窗口可能是主框架窗口、MDI 子窗口、标准控件、对话框、视图或某些其他类型的子窗口。

在运行时，每个窗口窗口均附加到 `CWnd` 具有其自己的关联消息映射和处理程序函数的窗口对象（直接或间接从派生）。 框架使用消息映射（对于命令）将传入消息映射到处理程序。

## <a name="see-also"></a>另请参阅

[框架如何调用处理程序](how-the-framework-calls-a-handler.md)
