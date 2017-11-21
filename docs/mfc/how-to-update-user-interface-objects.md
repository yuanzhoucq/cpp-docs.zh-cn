---
title: "如何： 更新用户界面对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 79a5b24c1e9d71f422748f4c6fb8cba97786462d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-update-user-interface-objects"></a>如何：更新用户界面对象
通常，菜单项和工具栏按钮有多个状态。 例如，如果菜单项在当前上下文中不可用，则将灰显（变暗）。 菜单项还可处于选中或未选中状态。 工具栏如果不可用也可处于禁用状态，否则它可处于选中状态。  
  
 谁将这些项，将在逻辑上，程序条件更改，如果菜单项生成由处理某个命令，例如，文档的状态更新，因此最好让文档更新菜单项。 文档可能包含更新所基于的信息。  
  
 如果命令具有多个用户界面对象（可能是一个菜单项和一个工具栏按钮），则这些对象将路由到同一处理程序函数。 这会将所有等效用户界面对象的用户界面更新代码封装在单个位置。  
  
 框架将为自动更新用户界面对象提供方便的界面。 您可以选择以某种其他方式进行更新，但提供的接口是高效且易于使用的。  
  
 下列主题介绍了更新处理程序的使用：  
  
-   [何时调用更新处理程序](../mfc/when-update-handlers-are-called.md)  
  
-   [ON_UPDATE_COMMAND_UI 宏](../mfc/on-update-command-ui-macro.md)  
  
-   [CCmdUI 类](../mfc/the-ccmdui-class.md)  
  
## <a name="see-also"></a>另请参阅  
 [菜单](../mfc/menus-mfc.md)

