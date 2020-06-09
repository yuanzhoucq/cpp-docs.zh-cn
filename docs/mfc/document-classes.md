---
title: 文档类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: 012d107d7bcc630c4bc02a9dc697172080787eac
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615806"
---
# <a name="document-classes"></a>文档类

文档类对象（由文档模板对象创建）管理应用程序的数据。 你将从这些类中的一个类派生你的文档的类。

文档类对象与视图对象交互。 视图对象表示窗口的工作区，显示文档的数据，并允许用户与之交互。 文档和视图由文档模板对象创建。

[CDocument](reference/cdocument-class.md)<br/>
特定于应用程序的文档的基类。 从派生您的文档类 `CDocument` 。

[COleDocument](reference/coledocument-class.md)<br/>
用于复合文档实现以及基本容器支持。 用作派生自[CDocItem](reference/cdocitem-class.md)的类的容器。 此类可用作容器文档的基类，并且是的基类 `COleServerDoc` 。

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
一个派生自 `COleDocument` 的类，它提供用于链接的基础结构。 应从此类派生容器应用程序的文档类，而不是从中派生 `COleDocument` 。

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
维护在 rich edit 控件中的 OLE 客户端项的列表。 与[CRichEditView](reference/cricheditview-class.md)和[CRichEditCntrItem](reference/cricheditcntritem-class.md)一起使用。

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
用作服务器应用程序文档类的基类。 `COleServerDoc`对象通过与[COleServerItem](reference/coleserveritem-class.md)对象的交互来提供大量服务器支持。 使用类库的文档/视图体系结构提供了可视编辑功能。

[CHtmlEditDoc](reference/chtmleditdoc-class.md)<br/>
通过[CHtmlEditView](reference/chtmleditview-class.md)，可以在 MFC 文档视图体系结构的上下文中提供 WebBrowser HTML 编辑平台的功能。

## <a name="related-classes"></a>相关类

文档类对象可能是持久性的，换言之，它们可以将其状态写入存储介质并重新读取。 MFC 提供 `CArchive` 类，以便于将文档数据传输到存储介质。

[CArchive](reference/carchive-class.md)<br/>
使用[CFile](reference/cfile-class.md)对象会通过序列化实现对象的持久存储（请参阅[CObject：：串行化](reference/cobject-class.md#serialize)）。

文档还可以包含 OLE 对象。 `CDocItem`服务器和客户端项的基类。

[CDocItem](reference/cdocitem-class.md)<br/>
[COleClientItem](reference/coleclientitem-class.md)和[COleServerItem](reference/coleserveritem-class.md)的抽象基类。 派生自的类的对象 `CDocItem` 表示文档的各个部分。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
