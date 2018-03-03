---
title: "将命令添加到菜单 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.menu
dev_langs:
- C++
helpviewer_keywords:
- menu items, adding to menus
- menus, adding items
- commands, adding to menus
- commands
- menu items
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d53f868fd76877152bb3ec81fdba85c1d97b3aac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-commands-to-a-menu"></a>将命令添加到菜单
### <a name="to-add-commands-to-a-menu"></a>将命令添加到菜单  
  
1.  [创建菜单](../windows/creating-a-menu.md)。  
  
2.  单击菜单名，例如“文件”。  
  
     每个菜单都将展开，并显示一个新项框让你输入命令。 例如，可以将“新建”、“打开”和“关闭”命令添加到“文件”菜单中。  
  
3.  在新项框中，键入新菜单命令的名称。  
  
    > [!NOTE]
    >  你键入的文本出现在菜单编辑器和在**标题**框中[属性窗口](/visualstudio/ide/reference/properties-window)。 你可以在任一位置编辑新菜单的属性。  
  
    > [!TIP]
    >  你可以定义一个允许用户选择菜单命令的助记键（热键）。 在字母前面键入 & 号，将它指定为助记键。 用户可以通过键入该字母来选择菜单命令。  
  
4.  在“属性”窗口中，选择适用的菜单命令属性。 有关详细信息，请参阅[菜单命令属性](../windows/menu-command-properties.md)。  
  
5.  在**提示符**框属性窗口中，键入你希望在应用程序的状态栏中显示的提示字符串。  
  
     这将在字符串表中创建一个条目，该条目的资源标识符与你创建的菜单命令相同。  
  
    > [!NOTE]
    >  提示只能应用于菜单项**弹出**属性**True**。 例如，包含子菜单项的顶级菜单项可以有提示。 提示的用途是告诉用户在单击菜单项时会发生什么事。  
  
6.  按**ENTER**完成菜单命令。  
  
     将选定新项框，让你可以创建其他菜单命令。  
  

  
 **要求**  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [菜单编辑器](../windows/menu-editor.md)   
