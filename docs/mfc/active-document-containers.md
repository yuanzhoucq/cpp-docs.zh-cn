---
title: 活动文档容器
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: dc7017a205bedd716e5c87aa23ac96b257af2e16
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626023"
---
# <a name="active-document-containers"></a>活动文档容器

活动文档容器（如 Microsoft Office 联编程序或 Internet Explorer）允许您在单个框架中处理不同应用程序类型的多个文档（而不是强制您为每个文档类型创建和使用多个应用程序框架）。

MFC 为类中的活动文档容器提供完全支持 `COleDocObjectItem` 。 您可以使用 MFC 应用程序向导创建活动文档容器，方法是在 MFC 应用程序向导的 "**复合文档支持**" 页上选中 "**活动文档容器**" 复选框。 有关详细信息，请参阅[创建活动文档容器应用程序](creating-an-active-document-container-application.md)。

有关活动文档容器的详细信息，请参阅：

- [容器要求](#container_requirements)

- [文档站点对象](#document_site_objects)

- [查看站点对象](#view_site_objects)

- 框选对象[](#frame_object)

- [帮助菜单合并](help-menu-merging.md)

- [编程打印](programmatic-printing.md)

- [命令目标](message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>容器要求

活动文档容器中的活动文档支持意味着不仅仅是接口实现：它还要求了解使用包含的对象的接口。 这同样适用于活动文档扩展，其中容器还必须知道如何在活动文档自身上使用这些扩展接口。

集成活动文档的活动文档容器必须：

- 可以通过接口处理对象存储 `IPersistStorage` ，也就是说，它必须 `IStorage` 为每个活动文档提供一个实例。

- 支持 OLE 文档的基本嵌入功能，即实现和的使得 "site" 对象（每个文档或嵌入一项） `IOleClientSite` `IAdviseSink` 。

- 支持嵌入对象或活动文档的就地激活。 容器的站点对象必须实现 `IOleInPlaceSite` 并且容器的帧对象必须提供 `IOleInPlaceFrame` 。

- 通过实现来支持活动文档的扩展， `IOleDocumentSite` 以便为容器提供与文档通信的机制。 容器还可以实现活动文档接口 `IOleCommandTarget` ，并可以 `IContinueCallback` 选取简单的命令，例如打印或保存。

帧对象、视图对象和容器对象可以选择实现 `IOleCommandTarget` 来支持调度特定命令，如[命令目标](message-handling-and-command-targets.md)中所述。 视图和容器对象还可以选择实现 `IPrint` 和 `IContinueCallback` ，以支持编程打印，如[编程打印](programmatic-printing.md)中所述。

下图显示容器及其组件（左侧）和活动文档及其视图（右侧）之间的概念关系。 活动文档管理存储和数据，视图显示或选择性地打印该数据。 以粗体显示的接口是活动文档参与所需的接口。粗体和斜体都是可选的。 所有其他接口都是必需的。

![活动文档容器接口](../mfc/media/vc37gj1.gif "活动文档容器接口")

仅支持一个视图的文档可在单个具体类上实现视图组件和文档组件（即它们对应的接口）。 此外，一次只支持一个视图的容器站点可以将文档站点和视图站点合并为一个具体的站点类。 不过，容器的帧对象必须保持不变，容器的文档组件只包含在此处以提供完整的体系结构，它不受活动文档包容体系结构的影响。

## <a name="document-site-objects"></a><a name="document_site_objects"></a>文档站点对象

在活动文档包容体系结构中，文档站点与 OLE 文档中的客户端站点对象相同，并添加了 `IOleDocument` 接口：

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

从概念上讲，文档站点是一个或多个 "查看站点" 对象的容器。 每个视图站点对象均与文档站点管理的文档的各个视图对象相关联。 如果容器仅支持每个文档站点的单个视图，则它可以实现文档站点和具有单个具体类的视图站点。

## <a name="view-site-objects"></a><a name="view_site_objects"></a>查看站点对象

容器的视图站点对象管理文档的特定视图的显示空间。 除了支持标准 `IOleInPlaceSite` 接口，视图站点通常还实现 `IContinueCallback` 了用于编程打印控件。 （请注意，视图对象从不会进行查询 `IContinueCallback` ，因此实际上可以在容器所需要的任何对象上实现它。）

支持多个视图的容器必须能够在文档网站中创建多个视图站点对象。 这将为每个视图提供单独的激活和停用服务，通过提供 `IOleInPlaceSite` 。

## <a name="frame-object"></a><a name="frame_object"></a>Frame 对象

在大多数情况下，容器的帧对象是用于在 OLE 文档中进行就地激活的相同帧，即处理菜单和工具栏协商的帧。 视图对象通过访问此框架对象 `IOleInPlaceSite::GetWindowContext` ，后者还提供对表示容器文档的容器对象（可以处理窗格级别的工具栏协商和包含的对象枚举）的访问。

活动文档容器可以通过添加来增加帧 `IOleCommandTarget` 。 这允许它接收源自活动文档的用户界面的命令，其方式与此接口允许容器发送相同命令（例如，**文件新建**、**打开**、**另存为**、**打印**;**编辑复制**、**粘贴**、**撤消**等）到活动文档。 有关详细信息，请参阅[命令目标](message-handling-and-command-targets.md)。

## <a name="see-also"></a>另请参阅

[活动文档包容](active-document-containment.md)
