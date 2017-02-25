---
title: "菜单和资源 (OLE) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序 [OLE], 菜单和资源"
  - "容器 [C++], OLE 容器应用程序"
  - "就地激活, OLE 菜单和资源"
  - "菜单 [C++], OLE 文档应用程序"
  - "OLE 应用程序 [C++], 菜单和资源"
  - "OLE 容器, 菜单和资源"
  - "OLE 菜单和资源"
  - "OLE 服务器应用程序, 菜单和资源"
  - "OLE 可视化编辑服务器"
  - "服务器应用程序, OLE 菜单和资源"
  - "状态栏, OLE 文档应用程序"
  - "字符串编辑, 可视化编辑应用程序"
  - "字符串表, 可视化编辑应用程序"
  - "工具栏 [C++], OLE 文档应用程序"
  - "可视化编辑, 应用程序菜单和资源"
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 菜单和资源 (OLE)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文章的此组说明使用菜单和资源的使用 MFC OLE 文档应用程序。  
  
 编辑菜单上的位置的其他要求和其他资源的 OLE 可视化对象提供由 OLE 文档应用程序，因为如果有容器和服务器的许多组件模式 \(\) 应用程序可以启动和使用。  例如，服务器应用程序可以在运行任何这三种模式：  
  
-   独立  
  
-   就地，用于编辑在容器的上下文内的项。  
  
-   为编辑在其容器外上下文中打开项，因此，通常在单独窗口。  
  
 这需要以下三个不同菜单布局，一个应用程序中的所有可能的模式。  快捷键对应表为每新模式也是必需的。  容器应用程序也可能不支持就地激活；如果是，它需要新的菜单结构和关联的快捷键对应表。  
  
 就地激活需要容器和服务器应用需要菜单、工具栏和状态栏空格协调。  必须记住此设计所有资源。  文章 [菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md) 详细包括本主题。  
  
 由于存在这些问题，OLE 文档应用程序创建与应用程序向导有四种不同菜单和快捷键表资源。  这些原因如下：  
  
|资源名称|使用|  
|----------|--------|  
|**IDR\_MAINFRAME**|使用在 MDI 应用程序中，如果文件无法打开，或者在 SDI 应用程序无论打开文件。  这是使用 OLE 非应用程序进行标准菜单。|  
|**IDR\_\<project\>TYPE**|使用在 MDI 应用程序，则文件打开。  使用，当应用程序是独立运行。  这是使用 OLE 非应用程序进行标准菜单。|  
|**IDR\_\<project\>TYPE\_SRVR\_IP**|使用按服务器或容器，当对象已准备就绪。|  
|**IDR\_\<project\>TYPE\_SRVR\_EMB**|使用按服务器应用，如果对象中打开，而无须使用就地激活。|  
  
 这些资源名称中的每一个都表示菜单，然后，通常是快捷键对应表。  一种类似的情况应在不会与应用程序向导的 MFC 应用程序。  
  
 下列文章讨论主题与容器，服务器和菜单合并需要实现就地激活：  
  
-   [菜单和资源：容器添加](../mfc/menus-and-resources-container-additions.md)  
  
-   [菜单和资源：服务器添加](../mfc/menus-and-resources-server-additions.md)  
  
-   [菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)  
  
## 请参阅  
 [OLE](../mfc/ole-in-mfc.md)