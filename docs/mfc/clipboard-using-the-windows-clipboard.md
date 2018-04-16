---
title: "剪贴板： 使用 Windows 剪贴板 |Microsoft 文档"
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
- Clipboard commands
- Cut/Copy and Paste command handler functions [MFC]
- handler functions, Cut/Copy and Paste commands
- Clipboard [MFC], commands
- commands [MFC], implementing Edit
- Clipboard commands [MFC], implementing
- Windows Clipboard [MFC]
- Clipboard [MFC], Windows Clipboard API
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6063a27495d46e4b54f3133b92689e4b0faaa631
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard-using-the-windows-clipboard"></a>剪贴板：使用 Windows 剪贴板
本主题介绍如何使用 MFC 应用程序中的标准 Windows 剪贴板 API。  
  
 适用于 Windows 的大多数应用程序支持剪切或将数据复制到 Windows 剪贴板和从剪贴板中粘贴数据。 剪贴板数据格式会因应用程序的不同而异。 框架支持有限数量的类仅有限的数量的剪贴板格式。 通常，您将实现剪贴板相关命令-剪切、 复制和粘贴-为您的视图的编辑菜单上。 类库定义了这些命令的命令 Id: **ID_EDIT_CUT**， **ID_EDIT_COPY**，和**ID_EDIT_PASTE**。 此外定义了其消息行提示。  
  
 [消息和框架中的命令](../mfc/messages-and-commands-in-the-framework.md)说明如何通过将菜单命令映射到处理程序函数来处理你的应用程序中的菜单命令。 在编辑菜单上，你的应用程序不会定义剪贴板命令的处理程序函数，只要它们保持禁用状态。 若要编写的剪切和复制命令的处理程序函数，请在你的应用程序中实现选择。 若要编写粘贴命令的处理程序函数，查询剪贴板，以便查看其是否包含你的应用程序可以接受的格式中的数据。 例如，若要启用复制命令，你可以编写处理程序类似于以下内容：  
  
 [!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]  
  
 剪切、 复制和粘贴命令才在某些上下文中有意义。 仅当选择了某些内容，粘贴命令仅当内容在剪贴板中时，应启用剪切和复制命令。 你可以通过定义更新处理程序函数，启用或禁用这些命令具体取决于上下文中提供此行为。 有关详细信息，请参阅[如何更新用户界面对象](../mfc/how-to-update-user-interface-objects.md)。  
  
 Microsoft 基础类库提供了剪贴板支持进行文本编辑使用`CEdit`和`CEditView`类。 OLE 类还简化了实现涉及 OLE 项的剪贴板操作。 OLE 类的详细信息，请参阅[剪贴板： 使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)。  
  
 实现其他编辑菜单命令，如撤消 (**ID_EDIT_UNDO**) 和重做 (**ID_EDIT_REDO**)，还从左到你。 如果你的应用程序不支持这些命令，因此你可以轻松地从资源文件使用 Visual c + + 资源编辑器删除它们。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [复制和粘贴数据](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
## <a name="see-also"></a>请参阅  
 [剪贴板](../mfc/clipboard.md)

