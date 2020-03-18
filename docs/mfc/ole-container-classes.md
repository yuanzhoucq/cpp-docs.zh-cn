---
title: OLE 容器类
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 61db5310637d13da2d2cc183f12f8f62aa60e328
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447653"
---
# <a name="ole-container-classes"></a>OLE 容器类

容器应用程序使用这些类。 `COleLinkingDoc` 和 `COleDocument` 管理 `COleClientItem` 对象的集合。 您将从 `COleLinkingDoc` 或 `COleDocument`派生您的文档类，而不是从 `CDocument`派生您的文档类，具体取决于您是否要支持指向嵌入到文档中的对象的链接。

使用 `COleClientItem` 对象来表示文档中从另一个文档嵌入的每个 OLE 项，或者是指向另一个文档的链接。

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
支持活动文档包容。

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
用于复合文档实现以及基本容器支持。 用作派生自 `CDocItem`的类的容器。 此类可用作容器文档的基类，并且是 `COleServerDoc`的基类。

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
一个派生自 `COleDocument` 的类，它提供用于链接的基础结构。 你应从此类派生容器应用程序的文档类，而不是从 `COleDocument` 中派生（如果你希望它们支持指向嵌入对象的链接）。

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
维护在 rich edit 控件中的 OLE 客户端项的列表。 与[CRichEditView](../mfc/reference/cricheditview-class.md)和[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)一起使用。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
`COleClientItem` 和 `COleServerItem`的抽象基类。 派生自 `CDocItem` 的类的对象表示文档的各个部分。

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
客户端项类，表示与嵌入或链接的 OLE 项的连接的客户端。 从此类派生客户端项。

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
当与 `CRichEditView` 和 `CRichEditDoc`一起使用时，提供对存储在 rich edit 控件中的 OLE 项的客户端访问。

[COleException](../mfc/reference/coleexception-class.md)<br/>
OLE 处理失败导致的异常。 此类将由容器和服务器使用。

## <a name="see-also"></a>另请参阅

[类概述](../mfc/class-library-overview.md)
