---
title: "剪贴板：使用 Windows 剪贴板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "剪贴板 [C++], 命令"
  - "剪贴板 [C++], Windows 剪贴板 API"
  - "剪贴板命令"
  - "剪贴板命令, 实现"
  - "命令 [C++], 实现编辑"
  - "剪切/复制和粘贴命令处理函数"
  - "处理函数, 剪切/复制和粘贴命令"
  - "Windows 剪贴板 [C++]"
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 剪贴板：使用 Windows 剪贴板
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此主题描述如何使用在 MFC 应用程序内的标准 Windows 剪贴板API。  
  
 对于窗口的大多数应用支持剪切或将数据复制到 Windows 剪贴板和粘贴剪贴板中的数据。  剪贴板数据格式在应用程序中不同。  框架支持有限数量类的仅限有限数量的剪贴板格式。  您通常实现剪贴板关联的命令 \- 剪切，复制，并将上 \- 在视图"编辑"菜单。  类库为这些命令定义命令 IDs: **ID\_EDIT\_CUT**、**ID\_EDIT\_COPY**和 **ID\_EDIT\_PASTE**。  其消息行提示还定义。  
  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md) 解释如何在你的应用程序中处理菜单命令通过映射菜单命令到处理函数  只要应用程序未为编辑菜单上的剪贴板命令定义处理函数，这些都保持禁用状态。  若要编写剪切和复制的命令处理程序函数，请在你的应用程序实现选择。  若要编写粘贴命令的处理程序函数，请查询剪贴板查看它是否在应用程序可以接受的格式包含数据。  例如，启用复制命令，您可能会编写处理程序类似于以下内容：  
  
 [!CODE [NVC_MFCListView#2](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCListView#2)]  
  
 剪切、复制和粘贴命令只有在特定上下文中才有意义。  仅在选择了某些内容时,剪切和复制命令应该启动，仅有东西在剪贴板时才会用到粘贴命令。  您可以通过定义更新一根据上下文能够启用或禁用这些命令的处理程序函数提供了此行为。  有关更多信息，请参见 [如何更新用户界面对象](../mfc/how-to-update-user-interface-objects.md)。  
  
 Microsoft 基础类库不提供剪贴板支持文本编辑使用 `CEdit` 和 `CEditView` 类。  OLE 类还简化实现涉及 OLE 项的剪贴板操作。  有关 OLE 类的更多信息，请参见 [剪贴板：使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)。  
  
 实现其他"编辑"菜单命令，如取消\(**ID\_EDIT\_UNDO**\) 和恢复 \(**ID\_EDIT\_REDO**\)，还保留给您。  如果应用程序不支持这些命令，可以使用 Visual C\+\+ 资源编辑器轻松地将它们从资源文件中删除。  
  
## 您想进一步了解什么？  
  
-   [复制和粘贴数据](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
## 请参阅  
 [剪贴板](../mfc/clipboard.md)