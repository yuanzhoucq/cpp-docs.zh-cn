---
title: 活动文档容器 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c912b6c703ef7e05825e070d09f0a1b3cd73003
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932154"
---
# <a name="active-document-containers"></a>活动文档容器
活动文档容器，如 Microsoft Office Binder 或 Internet Explorer 中，允许你使用不同的应用程序类型 （而不是强制你创建和使用多个应用程序帧每个单个范围内的多个文档文档类型）。  
  
 MFC 提供对中的活动文档容器的完全支持`COleDocObjectItem`类。 你可以使用 MFC 应用程序向导通过选择创建活动文档容器**活动文档容器**上的复选框**复合文档支持**MFC 应用程序向导页。 有关详细信息，请参阅[创建活动文档容器应用程序](../mfc/creating-an-active-document-container-application.md)。  
  
 活动文档容器有关的详细信息，请参阅：  
  
-   [容器要求](#container_requirements)  
  
-   [文档站点对象](#document_site_objects)  
  
-   [查看站点对象](#view_site_objects)  
  
-   [框选对象](#frame_object)  
  
-   [帮助菜单合并](../mfc/help-menu-merging.md)  
  
-   [以编程方式打印](../mfc/programmatic-printing.md)  
  
-   [命令目标](../mfc/message-handling-and-command-targets.md)  
  
##  <a name="container_requirements"></a> 容器要求  
 活动文档容器中的活动文档支持意味着以外的其他接口实现： 它还要求使用包含对象的接口的知识。 这同样适用于活动文档扩展，其中容器还必须了解如何使用活动文档自身上的这些扩展接口。  
  
 活动文档容器集成了活动文档必须：  
  
-   能够处理通过对象存储`IPersistStorage`接口，也就是说，它必须提供`IStorage`实例与每个活动文档。  
  
-   支持 OLE 文档，因而需要进行"站点"对象 （每个文档或嵌入的一个） 的基础嵌入功能实现`IOleClientSite`和`IAdviseSink`。  
  
-   支持就地激活嵌入的对象或活动文档。 容器的站点对象必须实现`IOleInPlaceSite`和容器的框架对象必须提供`IOleInPlaceFrame`。  
  
-   通过实现来支持活动文档的扩展`IOleDocumentSite`提供要与文档交流的容器的机制。 （可选） 容器可以实现活动文档接口`IOleCommandTarget`和`IContinueCallback`以拾取如打印或保存的简单命令。  
  
 框架对象、 对象的视图和容器对象 （可选） 可以实现`IOleCommandTarget`以支持中所述的某些命令的调度[命令目标](../mfc/message-handling-and-command-targets.md)。 视图和容器对象也可以实现`IPrint`和`IContinueCallback`，以便支持以编程方式打印，如下所述[以编程方式打印](../mfc/programmatic-printing.md)。  
  
 下图显示容器和其组件 （左侧） 和活动文档和其视图 （右侧） 之间的概念关系。 活动文档管理存储和数据，并显示的视图，或 （可选） 将打印该数据。 以粗体显示的接口是所需的活动文档参与;这些粗体和斜体是可选的。 所有其他接口是必需的。  
  
 ![活动文档容器接口](../mfc/media/vc37gj1.gif "vc37gj1")  
  
 支持单个视图的文档可以在单个具体类中实现的视图和文档的组件 （即，其相应的接口）。 此外，仅支持一次的一个视图的容器站点可以将文档站点和查看网站合并成单一的具体站点类。 但是，容器的框架对象，必须保留不同的并且容器的文档组件只是此处包括为提供的完整蓝图的体系结构;不受活动文档包容体系结构。  
  
##  <a name="document_site_objects"></a> 文档站点对象  
 在活动文档包容体系结构中，文档站点等同于客户端的站点对象在 OLE 文档中添加`IOleDocument`接口：  
  
 `interface IOleDocumentSite : IUnknown`  
  
 `{`  
  
 `HRESULT ActivateMe(IOleDocumentView *pViewToActivate);`  
  
 `}`  
  
 文档站点从概念上讲是一个或多个"查看站点"对象的容器。 每个视图站点对象都与文档由文档站点管理的单独的视图对象相关联。 如果容器仅支持每个文档站点的单一视图，，它可以实现文档站点和具有单个具体类的视图站点。  
  
##  <a name="view_site_objects"></a> 查看站点对象  
 容器的视图站点对象管理文档的特定视图的显示空间。 除了支持标准`IOleInPlaceSite`接口，查看网站也通常实现`IContinueCallback`以编程方式打印控件。 (请注意，视图对象永远不会查询为`IContinueCallback`因此它实际实现在容器需求的任何对象。)  
  
 支持多个视图的容器必须能够创建文档站点内的站点对象的多个视图。 这需要为每个视图提供了单独的激活和停用服务，如通过提供`IOleInPlaceSite`。  
  
##  <a name="frame_object"></a> 框架对象  
 容器的框架对象，大多数情况下，用于就地激活 OLE 文档中，它是同一帧、 处理菜单和工具栏协商。 视图对象有权访问通过此框架对象`IOleInPlaceSite::GetWindowContext`，其中还提供对表示容器文档 （它可以处理窗格级工具栏协商和包含的对象枚举） 的容器对象访问。  
  
 活动文档容器可以通过添加增强帧`IOleCommandTarget`。 这使它可以接收源自活动文档的用户界面与此接口可以允许一个容器来发送相同的命令相同的方式的命令 (如**文件新**，**打开**， **将另存为**，**打印**;**编辑副本**，**粘贴**，**撤消**，等) 到活动文档。 有关详细信息，请参阅[命令目标](../mfc/message-handling-and-command-targets.md)。  
  
## <a name="see-also"></a>请参阅  
 [活动文档包容](../mfc/active-document-containment.md)

