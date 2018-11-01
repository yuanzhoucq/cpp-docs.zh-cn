---
title: 映射消息
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], about message maps
- mappings [MFC], commands
- commands [MFC], mapping
- command mapping [MFC]
- message handling [MFC], connecting to handler functions
- commands [MFC], connecting to handler functions
- mappings [MFC], messages
- messages [MFC], mapping
ms.assetid: 996f0652-0698-4b8c-b893-cdaa836d9d0f
ms.openlocfilehash: 1f31bc2e3c6af9c4b899167ba99c152a231a929d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665837"
---
# <a name="mapping-messages"></a>映射消息

每个可以接收消息或命令的框架类都有自己的“消息映射”。 框架使用消息映射来将消息和命令连接到其处理程序函数。 派生自类 `CCmdTarget` 的所有类都可拥有消息映射。 其他文章详细解释了消息映射并说明了其使用方式。

尽管名称为"消息映射"映射可以同时处理的消息的消息和命令，所有三个类别的消息中列出[消息类别](../mfc/message-categories.md)。

## <a name="see-also"></a>请参阅

[框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)

