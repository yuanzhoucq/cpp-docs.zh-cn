---
title: 消息 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f25c9cc70cec598f975bbd242af83597311bdc7c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392250"
---
# <a name="messages"></a>消息

中的消息循环`Run`类的成员函数`CWinApp`检索生成的排队消息的各种事件。 例如，当用户单击鼠标，Windows 会发送多个与鼠标相关的消息，如 WM_LBUTTONDOWN 时按下鼠标左键和 WM_LBUTTONUP 释放鼠标按钮时。 应用程序消息循环的框架的实现会将消息调度到合适的窗口。

消息的重要类别中所述[消息类别](../mfc/message-categories.md)。

## <a name="see-also"></a>请参阅

[框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)

