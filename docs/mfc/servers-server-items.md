---
title: "服务器：服务器项 | Microsoft Docs"
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
  - "体系结构 [C++], 服务器项"
  - "OLE 服务器应用程序, 服务器项"
  - "服务器项"
  - "服务器项, 实现"
  - "服务器 [C++], 服务器项"
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 服务器：服务器项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当容器启动服务器，以便用户可编辑嵌入式或链接的 OLE 项，服务器应用创建“服务器项目”。服务器项目中，是派生自 `COleServerItem`的类对象，提供文档服务器和容器之间应用程序的接口。  
  
 `COleServerItem` 类通常定义受 OLE 调用的若干可重写的成员函数，而响应从容器的请求。  服务器项目可以表示一部分服务器文档或整个文档。  将 OLE 项容器中嵌入文档时，服务器项目表示整个服务器文档。  当 OLE 项链接时，服务器项目可以表示服务器文档或整个文档的部分，根据链接是部分还是全部。  
  
 在 [HIERSVR](../top/visual-cpp-samples.md) 示例，例如，服务器项类，具有 **CServerItem**，是指向类 **CServerNode**对象的一个成员。  **CServerNode** 对象在 HIERSVR 应用程序文档的一个节点，是棵树。  当 **CServerNode** 对象是根节点时，**CServerItem** 对象表示整个文档。  当 **CServerNode** 对象是子节点时，**CServerItem** 对象表示文档的一部分。  有关此函数的示例，请参见MFC OLE [HIERSVR](../top/visual-cpp-samples.md) 示例。  
  
##  <a name="_core_implementing_server_items"></a> 实现服务器项目  
 如果使用应用程序向导产生“应用程序的起始代码”，则必须对包含在程序启动的服务器项代码是选择某个服务器选项从 OLE 选项页的所有。  如果您将服务器项到现有应用程序，请执行以下步骤：  
  
#### 实现服务器项目  
  
1.  从 `COleServerItem` 派生一个类。  
  
2.  在派生类中，重写 `OnDraw` 成员函数。  
  
     `OnDraw` 呈现框架调用 OLE 项到图元文件。  容器应用程序使用此元文件呈现项。  应用程序的视图类还具有 `OnDraw` 成员函数，用于呈现项，当服务器应用是活动的。  
  
3.  服务器实现重写 `OnGetEmbeddedItem` 类的文档。  有关的详细信息，请参见 [服务器：实现服务器文档](../mfc/servers-implementing-server-documents.md) 文章和 MFC OLE 示例 [HIERSVR](../top/visual-cpp-samples.md)。  
  
4.  实现服务器项类的 `OnGetExtent` 成员函数。  框架调用该函数检索项的大小。  默认实现不执行任何操作。  
  
##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> 服务器项结构的提示  
 如 [实现服务器项目](#_core_implementing_server_items)中注明，服务器应用程序必须可以呈现在容器应用程序使用的元文件项的两个视图和在服务器中。  在 Microsoft 基础类库的应用程序体系结构中，视图类的 `OnDraw` 成员函数的方式呈现项，则在编辑时 \(请参见 [CView::OnDraw](../Topic/CView::OnDraw.md) 在 *类库参考*\)。  服务器项的 `OnDraw` 项元文件呈现到任何其他的情况 \(请参见 [COleServerItem::OnDraw](../Topic/COleServerItem::OnDraw.md)\)。  
  
 您可以通过中编写服务器类文档的帮助器函数和调用来避免复制的代码从在视图和服务器项类的 `OnDraw` 函数。  MFC OLE 示例 [HIERSVR](../top/visual-cpp-samples.md) 使用此策略：函数 **CServerView::OnDraw** 和 **CServerItem::OnDraw** 都调用 **CServerDoc::DrawTree** 的方式呈现项。  
  
 因为它们在不同条件下，绘制视图和项均具有 `OnDraw` 成员函数。  视图必须考虑这些因素进行缩放，以选择大小和范围、剪辑和用户界面元素 ，例如滚动条。  服务器项，另一方面，始终绘制整个 OLE 对象。  
  
 有关更多信息，请参见、[CView::OnDraw](../Topic/CView::OnDraw.md)[COleServerItem](../mfc/reference/coleserveritem-class.md)、[COleServerItem::OnDraw](../Topic/COleServerItem::OnDraw.md)和在  *类库引用*中的[COleServerDoc::OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md)。  
  
## 请参阅  
 [服务器](../mfc/servers.md)