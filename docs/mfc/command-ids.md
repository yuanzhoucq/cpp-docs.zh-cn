---
title: "命令 Id |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 95b531d12afc524e27bf36fc5a44d5f555fc9f91
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="command-ids"></a>命令 ID
命令完全由其单独的命令 ID (编码在**WM_COMMAND**消息)。 此 ID 分配给生成命令的用户界面对象。 通常情况下，分配给的用户界面对象的功能中名为 Id。  
  
 例如，编辑菜单中的全部清除项可能分配 ID 如**ID_EDIT_CLEAR_ALL**。 类库预定义了一些 Id，特别是对于命令，该框架将处理本身，如**ID_EDIT_CLEAR_ALL**或`ID_FILE_OPEN`。 你将自己创建其他命令 Id。  
  
 当你创建自己的菜单在 Visual c + + 菜单编辑器时，它是遵循類別庫一个好办法的命名约定，如图所示`ID_FILE_OPEN`。 [标准命令](../mfc/standard-commands.md)说明由类库所定义的标准命令。  
  
## <a name="see-also"></a>另请参阅  
 [用户界面对象和命令 ID](../mfc/user-interface-objects-and-command-ids.md)

