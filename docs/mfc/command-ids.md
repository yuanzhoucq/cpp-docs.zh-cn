---
title: 命令 ID
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: ecec4a7bd705dc74a3f45cc07da4abcdb168f43f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445625"
---
# <a name="command-ids"></a>命令 ID

命令完整描述了由其单独的命令 ID (以编码**WM_COMMAND**消息)。 此 ID 被分配给生成命令的用户界面对象。 通常情况下，Id 被命名的用户界面对象分配给他们的功能。

例如，在编辑菜单中的清除所有项可能都分配一个 ID 如**ID_EDIT_CLEAR_ALL**。 类库预定义了一些 Id，特别是对于命令，该框架将处理本身，如**ID_EDIT_CLEAR_ALL**或**ID_FILE_OPEN**。 您将自行创建其他命令 Id。

创建你自己的菜单在 Visual c + + 中菜单编辑器，时，最好遵循类库的命名约定，如所示**ID_FILE_OPEN**。 [标准命令](../mfc/standard-commands.md)介绍由类库定义的标准命令。

## <a name="see-also"></a>请参阅

[用户界面对象和命令 ID](../mfc/user-interface-objects-and-command-ids.md)

