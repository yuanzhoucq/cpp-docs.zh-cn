---
title: "活动文档容器 | Microsoft Docs"
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
  - "活动文档容器 [C++]"
  - "活动文档 [C++], 容器"
  - "容器 [C++], 活动文档"
  - "MFC COM [C++], 活动文档包容"
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 活动文档容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

活动文档容器，例如 Microsoft Office 活页夹或 Internet Explorer，可以使用不同的应用程序类型的多个文档。使用单个帧中 \(而不是强制您为每个文档类型创建和使用不同应用程序框架\)。  
  
 MFC 提供 `COleDocObjectItem` 类中的活动文档容器提供完全支持。  可以使用 MFC 应用程序向导。选择在 MFC 应用程序向导的 **复合文档支持** 页的 **活动文档容器 \(D\)** 复选框以创建活动文档容器。  有关更多信息，请参见 [创建活动文档容器应用程序](../mfc/creating-an-active-document-container-application.md)。  
  
 有关活动文档容器的更多信息，请参见：  
  
-   [容器要求](#container_requirements)  
  
-   [文档网站对象](#document_site_objects)  
  
-   [网站对象视图](#view_site_objects)  
  
-   [帧对象](#frame_object)  
  
-   [帮助菜单合并](../mfc/help-menu-merging.md)  
  
-   [编程打印](../mfc/programmatic-printing.md)  
  
-   [命令目标](../mfc/message-handling-and-command-targets.md)  
  
##  <a name="container_requirements"></a> 容器要求  
 在活动文档的活动文档容器支持暗指更多与接口实现：它还需要一包含的接口对象的知识。  同样适用于活动文档容器扩展，还必须将使用活动文档的某些扩展接口。  
  
 集成活动文档的活动文档容器必须：  
  
-   能够处理对象存储通过 **IPersistStorage** 接口，即，它必须提供 `IStorage` 实例为每个活动文档。  
  
-   支持 OLE 文档基础的嵌入功能，需要“网站”对象 \(每个嵌入文档或\) 实现 **IOleClientSite** 和 **IAdviseSink**。  
  
-   嵌入对象或活动文档支持就地激活。  容器的网站对象必须实现 `IOleInPlaceSite`，并且该容器的帧对象必须提供 **IOleInPlaceFrame**。  
  
-   通过实现 `IOleDocumentSite` 来提供机制活动文档容器支持的扩展与文档可用。  或者，可以实现活动文档容器接口 `IOleCommandTarget` 和 `IContinueCallback` 包含简单命令 \(如打印或保存。  
  
 帧、对象和视图对象容器对象可以选择实现 **IOleCommandTarget** 某些支持命令安排，如 [命令目标](../mfc/message-handling-and-command-targets.md)所述。  视图和容器对象还可以实现 `IPrint` 和 `IContinueCallback`，则支持的编程打印，如 [编程打印](../mfc/programmatic-printing.md)所述。  
  
 下图显示容器及其组件之间关系的概念 \(左侧\) 和活动文档及其视图。\(右侧\)。  活动文档管理存储和数据，并显示视图，或选择数据的打印。  在粗体的接口是活动文档。参与是必需的；一些粗体和斜体是可选的。  需要的其他接口。  
  
 ![活动文档容器接口](../mfc/media/vc37gj1.png "vc37gj1")  
  
 只支持单一文档的视图来实现视图和文档组件 \(即它的对应接口\) 在一台物理类别。  此外，一次只支持一视图的容器可将网站文档网站和站点视图到单个站点特定类。  容器的帧对象，但是，必须保持标记，并且，容器文档组件仅包含此处为体系结构的完整样式；不影响的受活动文档包容结构的。  
  
##  <a name="document_site_objects"></a> 文档网站对象  
 在活动文档包容结构中，文档网站与在 OLE 文档的客户端网站对象添加了 `IOleDocument` 接口相同的：  
  
 `interface IOleDocumentSite : IUnknown`  
  
 `{`  
  
 `HRESULT ActivateMe(IOleDocumentView *pViewToActivate);`  
  
 `}`  
  
 文档网站从概念上讲是一个或多个“视图的”对象的容器。  每个视图的网站对象与网站管理文档的文档的各个视图对象。  如果容器只支持单个视图每个文档网站，则可以实现网站文档和视图站点具有唯一物理类别的。  
  
##  <a name="view_site_objects"></a> 网站对象视图  
 网站管理文档容器的视图对象的特定视图的显示空间。  除了标准支持 `IOleInPlaceSite` 接口外，网站通常视图还实现编程打印控件的 `IContinueCallback`。\(视图对象。`IContinueCallback` 从查询的注释，因此对容器所需\) 的所有对象的实际实现  
  
 支持多视图的容器必须能够在创建文档网站内的多个视图的网站对象。  这提供每个视图。单独激活与停用服务根据通过提供 `IOleInPlaceSite`。  
  
##  <a name="frame_object"></a> 帧对象  
 容器的帧对象是，大多，对于就地激活在 OLE 文档，即，一个用于处理菜单和工具栏协商相同的帧。  对象视图对此的帧对象通过 **IOleInPlaceSite::GetWindowContext**，也提供对表示文档容器 \(的容器对象可以处理级别和协商窗格工具栏包含的对象枚举\)。  
  
 活动文档容器可以通过将 `IOleCommandTarget`增加帧。  这使它可以接收的方式与自在活动文档的用户界面的命令此接口可以允许发送相同容器命令 \(如 **File New**，**打开**，**打印**; **另存为**，**Edit Copy**、**粘贴**，**撤消**和其他一些函数\) 到活动文档。  有关更多信息，请参见 [命令目标](../mfc/message-handling-and-command-targets.md)。  
  
## 请参阅  
 [活动文档包容](../mfc/active-document-containment.md)