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
ms.openlocfilehash: 16d6d7725d82bed6c9bfc02e408b68dcf7ffe5e4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625489"
---
# <a name="mapping-messages"></a>映射消息

每个可以接收消息或命令的框架类都有自己的“消息映射”。 框架使用消息映射来将消息和命令连接到其处理程序函数。 派生自类 `CCmdTarget` 的所有类都可拥有消息映射。 其他文章详细解释了消息映射并说明了其使用方式。

尽管名称为 "消息映射"，但消息映射会同时处理消息和命令（[消息类别](message-categories.md)中列出的所有三类消息。

## <a name="see-also"></a>另请参阅

[框架中的消息和命令](messages-and-commands-in-the-framework.md)
