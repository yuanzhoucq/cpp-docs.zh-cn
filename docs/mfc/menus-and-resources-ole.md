---
title: 菜单和资源 (OLE) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE visual editing servers [MFC]
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- string tables [MFC], visual editing applications
- OLE containers [MFC], menus and resources
- OLE applications [MFC], menus and resources
- OLE server applications [MFC], menus and resources
- toolbars [MFC], OLE document applications
- string editing [MFC], visual editing applications
- server applications [MFC], OLE menus and resources
- applications [OLE], menus and resources
- menus [MFC], OLE document applications
- in-place activation [MFC], OLE menus and resources
- containers [MFC], OLE container applications
- OLE menus and resources [MFC]
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efe0a5f6dae2cece571eddabc4094ebb87df175b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="menus-and-resources-ole"></a>菜单和资源 (OLE)
此系列文章介绍了使用菜单和 MFC OLE 文档应用程序中的资源。  
  
 OLE 可视化编辑对其他要求菜单和其他资源由 OLE 文档应用程序，因为有大量的这两个容器中的模式和服务器 （组件） 应用程序可以启动和使用。 例如，完全服务器应用程序可以在任何这些三种模式中运行：  
  
-   单独。  
  
-   结构，以进行编辑上下文中的容器的项。  
  
-   打开，以进行编辑其容器，通常在单独的窗口的上下文之外的项。  
  
 这需要三个不同的菜单布局，一个用于应用程序的每个可能的模式。 快捷键表也是必需的每个新的模式。 容器应用程序可能或可能不支持就地激活;如果是这样，它将需要新的菜单结构和关联的快捷键对应表。  
  
 就地激活要求容器和服务器应用程序必须协商菜单、 工具栏和状态栏空间。 记住，必须与此设计的所有资源。 文章[菜单和资源： 菜单合并](../mfc/menus-and-resources-menu-merging.md)介绍本主题中详细信息。  
  
 鉴于这些问题，使用应用程序向导创建 OLE 文档应用程序可以具有最多四个单独的菜单和快捷键对应表资源。 由于以下原因需要使用这些：  
  
|资源名称|使用|  
|-------------------|---------|  
|**IDR_MAINFRAME**|用于 MDI 应用程序是否没有文件处于打开状态，或 SDI 应用程序而不考虑打开的文件中。 这是在非 OLE 应用程序中使用的标准菜单。|  
|**IDR_\<项目 > 类型**|如果文件处于打开状态，在 MDI 应用程序中使用。 应用程序以独立模式运行时使用。 这是在非 OLE 应用程序中使用的标准菜单。|  
|**IDR_\<项目 > TYPE_SRVR_IP**|当对象处于打开位置时使用的服务器或容器。|  
|**IDR_\<项目 > TYPE_SRVR_EMB**|如果不使用就地激活打开对象服务器应用程序使用。|  
  
 其中每个资源名称表示菜单和快捷键对应表，通常情况下。 应在不使用应用程序向导创建的 MFC 应用程序使用类似的方案。  
  
 以下文章介绍了与容器、 服务器和菜单合并需要实现就地激活相关的主题：  
  
-   [菜单和资源：容器添加](../mfc/menus-and-resources-container-additions.md)  
  
-   [菜单和资源：服务器添加](../mfc/menus-and-resources-server-additions.md)  
  
-   [菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)  
  
## <a name="see-also"></a>请参阅  
 [OLE](../mfc/ole-in-mfc.md)

