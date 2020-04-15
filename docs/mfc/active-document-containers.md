---
title: 活动文档容器
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: e2005ffed592fa1de278e0f6339d94687a20fd06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377386"
---
# <a name="active-document-containers"></a>活动文档容器

活动文档容器（如 Microsoft Office Binder 或 Internet Explorer）允许您在单个框架中使用多个不同应用程序类型的文档（而不是强制为每个文档类型创建和使用多个应用程序框架）。

MFC 为类中的`COleDocObjectItem`活动文档容器提供完全支持。 您可以通过在 MFC 应用程序向导的**复合文档支持**页上选择 **"活动文档容器**"复选框，使用 MFC 应用程序向导创建活动文档容器。 有关详细信息，请参阅[创建活动文档容器应用程序](../mfc/creating-an-active-document-container-application.md)。

有关活动文档容器的详细信息，请参阅：

- [集装箱要求](#container_requirements)

- [文档站点对象](#document_site_objects)

- [查看站点对象](#view_site_objects)

- 框选对象[](#frame_object)

- [帮助菜单合并](../mfc/help-menu-merging.md)

- [编程打印](../mfc/programmatic-printing.md)

- [命令目标](../mfc/message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>集装箱要求

活动文档容器中的活动文档支持不仅仅意味着接口实现：它还需要使用包含对象的接口的知识。 这同样适用于活动文档扩展，其中容器还必须知道如何在活动文档本身上使用这些扩展接口。

集成活动文档的活动文档容器必须：

- 能够通过`IPersistStorage`接口处理对象存储，也就是说，它必须为每个活动文档提供实例`IStorage`。

- 支持 OLE 文档的基本嵌入功能，需要实现`IOleClientSite`和`IAdviseSink`的"站点"对象（每个文档或嵌入一个）。

- 支持就地激活嵌入对象或活动文档。 容器的站点对象必须实现`IOleInPlaceSite`，容器的帧对象必须提供`IOleInPlaceFrame`。

- 通过实现`IOleDocumentSite`为容器提供与文档对话的机制，支持活动文档的扩展。 或者，容器可以实现活动文档接口`IOleCommandTarget`，并`IContinueCallback`拾取简单的命令，如打印或保存。

框架对象、视图对象和容器对象可以选择实现`IOleCommandTarget`以支持某些命令的调度，如[命令目标](../mfc/message-handling-and-command-targets.md)中所述。 视图和容器对象也可以选择实现`IPrint`和`IContinueCallback`，以支持编程打印，如[编程打印](../mfc/programmatic-printing.md)中所述。

下图显示了容器及其组件（左图）与活动文档及其视图（右侧）之间的概念关系。 活动文档管理存储和数据，视图显示或选择性地打印该数据。 粗体界面是主动参与文档所需的接口;这些粗体和斜体是可选的。 所有其他接口是必需的。

![活动文档容器接口](../mfc/media/vc37gj1.gif "活动文档容器接口")

仅支持单个视图的文档可以在单个具体类上实现视图和文档组件（即其相应的接口）。 此外，一次仅支持一个视图的容器站点可以将文档站点和视图站点合并到单个具体站点类中。 但是，容器的帧对象必须保持不同，并且容器的文档组件仅在此处包含，以便完整地反映体系结构;它不受活动文档包含体系结构的影响。

## <a name="document-site-objects"></a><a name="document_site_objects"></a>文档站点对象

在活动文档包含体系结构中，文档站点与 OLE 文档中的客户端站点对象相同，并添加`IOleDocument`接口：

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

文档站点在概念上是一个或多个"查看站点"对象的容器。 每个视图网站对象都与文档站点管理的文档的各个视图对象相关联。 如果容器仅支持每个文档站点的单个视图，则可以使用单个具体类实现文档站点和视图站点。

## <a name="view-site-objects"></a><a name="view_site_objects"></a>查看站点对象

容器的视图站点对象管理文档的特定视图的显示空间。 除了支持标准`IOleInPlaceSite`接口外，视图站点通常还实现了`IContinueCallback`编程打印控制。 （请注意，视图对象从不查询`IContinueCallback`，因此它实际上可以在容器所需的任何对象上实现。

支持多个视图的容器必须能够在文档站点内创建多个视图站点对象。 这为每个视图提供了通过`IOleInPlaceSite`提供的单独激活和停用服务。

## <a name="frame-object"></a><a name="frame_object"></a>帧对象

容器的帧对象在大多数情况下与用于在 OLE 文档中就地激活的帧相同，即处理菜单和工具栏协商的框架。 视图对象可通过`IOleInPlaceSite::GetWindowContext`访问此帧对象，该对象还提供对表示容器文档的容器对象的访问（该对象可以处理窗格级工具栏协商和包含的对象枚举）。

活动文档容器可以通过添加`IOleCommandTarget`来增强帧。 这允许它接收源自活动文档用户界面的命令，就像此接口允许容器发送相同的命令（如**文件新**、**打开**、**保存为**、**打印**等命令） 一样。**将"复制**"、"**粘贴**"、"**撤消**"等编辑到活动文档。 有关详细信息，请参阅[命令目标](../mfc/message-handling-and-command-targets.md)。

## <a name="see-also"></a>另请参阅

[活动文档包含](../mfc/active-document-containment.md)
