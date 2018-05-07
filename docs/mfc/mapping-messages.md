---
title: 将消息映射 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f521145599a3d734a22dd3b2707ad4dd16df8e80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mapping-messages"></a>映射消息
每个可以接收消息或命令的框架类都有自己的“消息映射”。 框架使用消息映射来将消息和命令连接到其处理程序函数。 派生自类 `CCmdTarget` 的所有类都可拥有消息映射。 其他文章详细解释了消息映射并说明了其使用方式。  
  
 存在名称为"消息映射"消息映射可以同时处理消息和命令-的消息中列出的所有三个类别[消息类别](../mfc/message-categories.md)。  
  
## <a name="see-also"></a>请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)

