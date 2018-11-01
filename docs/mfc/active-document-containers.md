---
title: 活动文档容器
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: ec2e4d11e00040cf0b94957db8466d127e0b5420
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510833"
---
# <a name="active-document-containers"></a>活动文档容器

活动文档容器，如 Microsoft Office Binder 或 Internet Explorer 中，可以使用不同的应用程序中的类型 （而不是强制您创建和使用应用程序的多个框架为每个单个帧的多个文档文档类型）。

MFC 提供对中的活动文档容器的完全支持`COleDocObjectItem`类。 可以使用 MFC 应用程序向导来创建活动文档容器通过选择**活动文档容器**上的复选框**复合文档支持**MFC 应用程序向导的页。 有关详细信息，请参阅[创建活动文档容器应用程序](../mfc/creating-an-active-document-container-application.md)。

关于活动文档容器的详细信息，请参阅：

- [容器要求](#container_requirements)

- [文档站点对象](#document_site_objects)

- [查看站点对象](#view_site_objects)

- [框选对象](#frame_object)

- [帮助菜单合并](../mfc/help-menu-merging.md)

- [以编程方式打印](../mfc/programmatic-printing.md)

- [命令目标](../mfc/message-handling-and-command-targets.md)

##  <a name="container_requirements"></a> 容器要求

活动文档容器中的活动文档支持意味着不仅仅接口实现： 它还需要了解如何使用所包含的对象的接口。 这同样适用于活动文档扩展，其中该容器还必须知道如何对在活动文档中自行使用这些扩展插件接口。

活动文档容器集成了活动文档必须：

- 为能够处理对象存储，一直`IPersistStorage`接口，即，它必须提供`IStorage`实例与每个活动文档。

- 支持 OLE 文档，需要"站点"对象 （每个文档或嵌入一个） 的基础嵌入功能实现`IOleClientSite`和`IAdviseSink`。

- 支持就地激活嵌入的对象或活动文档。 容器的站点对象必须实现`IOleInPlaceSite`和容器的框架对象必须提供`IOleInPlaceFrame`。

- 通过实现来支持活动文档的扩展`IOleDocumentSite`提供与文档的容器的机制。 容器 （可选） 可以实现活动文档接口`IOleCommandTarget`和`IContinueCallback`选取简单的命令，如打印或保存。

框架对象、 对象的视图和容器对象可以选择实现`IOleCommandTarget`中所述支持的某些命令调度[命令目标](../mfc/message-handling-and-command-targets.md)。 可以选择性地实现视图和容器对象`IPrint`并`IContinueCallback`，以支持以编程方式打印，如中所述[以编程方式打印](../mfc/programmatic-printing.md)。

下图显示了容器和其组件 （左侧） 和活动文档和其视图 （右侧） 之间的概念关系。 活动文档管理存储和数据，并查看显示或或者打印数据。 以粗体显示的接口是所需的活动文档的参与;这些粗体和斜体是可选的。 所有其他接口是必需的。

![活动文档容器接口](../mfc/media/vc37gj1.gif "vc37gj1")

支持单个视图的文档可以在单个具体类实现的视图和文档组件 （即，相应的接口）。 此外，仅支持一次一个视图的容器站点可以将文档站点以及查看网站结合到单个具体站点类。 但是，容器的框架对象必须完全不同，和容器的文档组件只是此处包含为提供完整的体系结构; 图不受活动文档包容体系结构。

##  <a name="document_site_objects"></a> 文档站点对象

在活动文档包容体系结构中，文档站点等同于客户端的站点对象中 OLE 文档添加了`IOleDocument`接口：

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

文档站点从概念上讲是一个或多个"查看站点"对象的容器。 查看站点的每个对象都具有单独的视图对象的文档站点所管理的文档相关联。 如果容器仅支持每个文档站点的单一视图，，它可以实现文档站点和使用单个具体类查看网站。

##  <a name="view_site_objects"></a> 查看站点对象

容器的视图站点对象管理文档的特定视图的显示空间。 除了支持标准`IOleInPlaceSite`接口，查看网站通常也实现`IContinueCallback`以编程方式打印控件。 (请注意，视图对象永远不会查询`IContinueCallback`以便实际上实现容器需求的任何对象。)

支持多个视图的容器必须能够创建多个视图中的文档站点的站点对象。 这需要为每个视图提供了单独的激活和停用服务，如通过提供`IOleInPlaceSite`。

##  <a name="frame_object"></a> 框选对象

容器的框架对象是，大多数情况下，用于在 OLE 文档中的就地激活，它是同一帧、 处理菜单和工具栏协商。 视图对象有权访问通过此帧对象`IOleInPlaceSite::GetWindowContext`，它还提供对容器对象表示容器文档 （它可以处理窗格级工具栏协商和包含的对象枚举） 的访问。

活动文档容器可以通过添加来扩充帧`IOleCommandTarget`。 这使得它可以接收源自活动文档的用户界面中相同的方式，此接口可以允许一个容器，以发送相同的命令的命令 (如**文件新建**，**打开**， **将另存为**，**打印**;**编辑副本**，**粘贴**，**撤消**，等等) 到活动文档。 有关详细信息，请参阅[命令目标](../mfc/message-handling-and-command-targets.md)。

## <a name="see-also"></a>请参阅

[活动文档包容](../mfc/active-document-containment.md)

