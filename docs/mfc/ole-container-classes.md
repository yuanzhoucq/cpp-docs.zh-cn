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
ms.openlocfilehash: 596b94e7fdbb5d9dc1862867001f6c01c1aea7b2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617799"
---
# <a name="ole-container-classes"></a>OLE 容器类

容器应用程序使用这些类。 `COleLinkingDoc`和都 `COleDocument` 管理对象的集合 `COleClientItem` 。 您将从或派生您的文档类，而不是从派生您的文档类 `CDocument` `COleLinkingDoc` `COleDocument` ，具体取决于您是否要支持指向嵌入到文档中的对象的链接。

使用 `COleClientItem` 对象表示文档中从另一个文档嵌入的每个 OLE 项，或者是指向另一个文档的链接。

[COleDocObjectItem](reference/coledocobjectitem-class.md)<br/>
支持活动文档包容。

[COleDocument](reference/coledocument-class.md)<br/>
用于复合文档实现以及基本容器支持。 用作派生自的类的容器 `CDocItem` 。 此类可用作容器文档的基类，并且是的基类 `COleServerDoc` 。

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
一个派生自 `COleDocument` 的类，它提供用于链接的基础结构。 应从此类派生容器应用程序的文档类，而不是从中派生 `COleDocument` 。

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
维护在 rich edit 控件中的 OLE 客户端项的列表。 与[CRichEditView](reference/cricheditview-class.md)和[CRichEditCntrItem](reference/cricheditcntritem-class.md)一起使用。

[CDocItem](reference/cdocitem-class.md)<br/>
和的抽象基类 `COleClientItem` `COleServerItem` 。 派生自的类的对象 `CDocItem` 表示文档的各个部分。

[COleClientItem](reference/coleclientitem-class.md)<br/>
客户端项类，表示与嵌入或链接的 OLE 项的连接的客户端。 从此类派生客户端项。

[CRichEditCntrItem](reference/cricheditcntritem-class.md)<br/>
当与和一起使用时，提供对存储在 rich edit 控件中的 OLE 项的客户端访问 `CRichEditView` `CRichEditDoc` 。

[COleException](reference/coleexception-class.md)<br/>
OLE 处理失败导致的异常。 此类将由容器和服务器使用。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
