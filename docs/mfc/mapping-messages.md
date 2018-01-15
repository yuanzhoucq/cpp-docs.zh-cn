---
title: "将消息映射 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c415b12b22c19a5e1f2d19fd9c808a98485eb7ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-messages"></a>映射消息
每个可以接收消息或命令的框架类都有自己的“消息映射”。 框架使用消息映射来将消息和命令连接到其处理程序函数。 派生自类 `CCmdTarget` 的所有类都可拥有消息映射。 其他文章详细解释了消息映射并说明了其使用方式。  
  
 存在名称为"消息映射"消息映射可以同时处理消息和命令-的消息中列出的所有三个类别[消息类别](../mfc/message-categories.md)。  
  
## <a name="see-also"></a>请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)

