---
title: 用户界面对象和命令 ID
ms.date: 11/19/2018
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
ms.openlocfilehash: 54372facc51062add122c1db2e01e3081127512e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180594"
---
# <a name="user-interface-objects-and-command-ids"></a>用户界面对象和命令 ID

菜单项、工具栏按钮和快捷键是能够生成命令的“用户界面对象”。 每个此类用户界面对象都有一个 ID。 您可通过为用户界面对象和命令分配同一 ID 来将它们关联。 中所述[消息](../mfc/messages.md)，命令作为特殊消息实现。 下面的图“Framework 中的命令”演示了框架如何管理命令。 当用户界面对象生成某个命令（如 `ID_EDIT_CLEAR_ALL`）时，应用程序中的对象之一将处理命令 - 在下图中，将通过文档的消息映射调用文档对象的 `OnEditClearAll`。

![框架中的命令](../mfc/media/vc385p1.gif "框架中的命令") <br/>
框架中的命令

下面的图“框架中的命令更新”演示了 MFC 如何更新用户界面对象（如菜单项和工具栏按钮）。 在菜单下拉前，或者在工具栏按钮空闲循环期间，MFC 将传递更新命令。 在下图中，文档对象调用其更新命令处理程序 `OnUpdateEditClearAll` 来启用或禁用用户界面对象。

![命令框架中的更新](../mfc/media/vc385p2.png "命令框架中的更新") <br/>
框架中的命令更新

## <a name="see-also"></a>请参阅

[框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)
