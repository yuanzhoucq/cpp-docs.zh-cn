---
title: "用户界面对象和命令 Id |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e085c6d9e4d030c8db44e11e570ffa1033abee35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="user-interface-objects-and-command-ids"></a>用户界面对象和命令 ID
菜单项、工具栏按钮和快捷键是能够生成命令的“用户界面对象”。 每个此类用户界面对象都有一个 ID。 您可通过为用户界面对象和命令分配同一 ID 来将它们关联。 中所述[消息](../mfc/messages.md)，命令作为特殊消息实现。 下面的图“Framework 中的命令”演示了框架如何管理命令。 当用户界面对象生成某个命令（如 `ID_EDIT_CLEAR_ALL`）时，应用程序中的对象之一将处理命令 - 在下图中，将通过文档的消息映射调用文档对象的 `OnEditClearAll`。  
  
 ![框架中的命令](../mfc/media/vc385p1.gif "vc385p1")  
框架中的命令  
  
 下面的图“框架中的命令更新”演示了 MFC 如何更新用户界面对象（如菜单项和工具栏按钮）。 在菜单下拉前，或者在工具栏按钮空闲循环期间，MFC 将传递更新命令。 在下图中，文档对象调用其更新命令处理程序 `OnUpdateEditClearAll` 来启用或禁用用户界面对象。  
  
 ![命令框架中的更新](../mfc/media/vc385p2.png "vc385p2")  
框架中的命令更新  
  
## <a name="see-also"></a>请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)

