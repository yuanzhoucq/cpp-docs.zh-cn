---
title: 消息
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: f36dab679a2e41910b2445a7dab36f5786081563
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624285"
---
# <a name="messages"></a>消息

类的成员函数中的消息循环 `Run` `CWinApp` 检索由各种事件生成的已排队消息。 例如，当用户单击鼠标时，Windows 将发送多个与鼠标相关的消息，例如在按下鼠标左键时 WM_LBUTTONDOWN，并在释放鼠标左键时 WM_LBUTTONUP。 应用程序消息循环的框架的实现会将消息调度到合适的窗口。

[消息类别](message-categories.md)中描述了重要的消息类别。

## <a name="see-also"></a>另请参阅

[框架中的消息和命令](messages-and-commands-in-the-framework.md)
