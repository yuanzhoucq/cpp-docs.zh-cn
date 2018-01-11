---
title: "服务器： 实现服务器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 148a3da3c904f5c314c75fb71deede3c92163cc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="servers-implementing-a-server"></a>服务器：实现服务器
此文章介绍了 MFC 应用程序向导为可视化编辑服务器应用程序创建的代码。 如果你未使用应用程序向导，本文列出了，你必须编写代码来实现服务器应用程序的区域。  
  
 如果将应用程序向导创建新的服务器应用程序，它为你提供大量的特定服务器的代码。 如果你将可视化编辑服务器功能添加到现有应用程序，你必须重复的应用程序向导将添加必要的服务器代码的其余部分之前提供的代码。  
  
 应用程序向导提供的服务器代码划分为多个类别：  
  
-   定义服务器资源：  
  
    -   服务器正在编辑自己的窗口中的嵌入的项时使用的菜单资源。  
  
    -   使用服务器处于就地活动状态时的菜单和工具栏资源。  
  
     对这些资源的详细信息，请参阅[菜单和资源： 服务器添加](../mfc/menus-and-resources-server-additions.md)。  
  
-   定义一个项类派生自`COleServerItem`。 服务器项的更多详细信息，请参阅[服务器： 服务器项](../mfc/servers-server-items.md)。  
  
-   更改文档类的基类`COleServerDoc`。 有关更多详细信息，请参阅[服务器： 实现服务器文档](../mfc/servers-implementing-server-documents.md)。  
  
-   定义的框架窗口类派生自`COleIPFrameWnd`。 有关更多详细信息，请参阅[服务器： 实现就地框架窗口](../mfc/servers-implementing-in-place-frame-windows.md)。  
  
-   在 Windows 注册数据库中创建服务器应用程序的条目，并向 OLE 系统注册的服务器的新实例。 本主题的信息，请参阅[注册](../mfc/registration.md)。  
  
-   初始化和启动服务器应用程序。 本主题的信息，请参阅[注册](../mfc/registration.md)。  
  
 有关详细信息，请参阅[COleServerItem](../mfc/reference/coleserveritem-class.md)， [COleServerDoc](../mfc/reference/coleserverdoc-class.md)，和[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)中*类库参考*。  
  
## <a name="see-also"></a>请参阅  
 [服务器](../mfc/servers.md)   
 [容器](../mfc/containers.md)   
 [菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)   
 [注册](../mfc/registration.md)

