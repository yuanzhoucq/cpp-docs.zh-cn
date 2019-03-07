---
title: 文档类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: a7034a99bfefe8f4c11cdf8f99dc4b0c31fac10a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289710"
---
# <a name="document-classes"></a>文档类

创建的文档模板对象的文档类对象管理应用程序的数据。 从这些类之一，将为你的文档中派生一个类。

文档类对象与视图对象进行交互。 视图对象表示一个窗口的工作区，显示文档的数据，并使用户可以与其进行交互。 文档模板对象的情况下，将创建文档和视图。

[CDocument](../mfc/reference/cdocument-class.md)<br/>
特定于应用程序的文档的基类。 从派生文档类`CDocument`。

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
用于复合文档实现，以及基本容器支持。 可用作容器的类派生自[CDocItem](../mfc/reference/cdocitem-class.md)。 此类可以用作基类，为容器记录，并且是类的基类`COleServerDoc`。

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
一个类派生自`COleDocument`为链接提供了基础结构。 应为此类，而不是从容器应用程序派生文档类`COleDocument`如果你希望它们以支持链接到嵌入对象。

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
维护格式文本编辑控件中的 OLE 客户端项的列表。 用于[CRichEditView](../mfc/reference/cricheditview-class.md)并[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
用作服务器应用程序文档类的基类。 `COleServerDoc` 对象提供的与的交互通过服务器支持批量[COleServerItem](../mfc/reference/coleserveritem-class.md)对象。 使用类库的文档/视图体系结构提供可视编辑功能。

[CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)<br/>
提供了，与[CHtmlEditView](../mfc/reference/chtmleditview-class.md)，MFC 文档视图体系结构的上下文中的 webbrowser 控件中 HTML 编辑平台功能。

## <a name="related-classes"></a>相关的类

文档类对象可以是永久性的即，它们可以将其状态写入到存储介质和读回。 MFC 提供了`CArchive`类以方便在文档的数据传输到存储介质。

[CArchive](../mfc/reference/carchive-class.md)<br/>
所以会与协作[CFile](../mfc/reference/cfile-class.md)对象来实现通过序列化对象的持久性存储区 (请参阅[cobject:: Serialize](../mfc/reference/cobject-class.md#serialize))。

文档还包含 OLE 对象。 `CDocItem` 是服务器和客户端项的基类。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
抽象类的基类[COleClientItem](../mfc/reference/coleclientitem-class.md)并[COleServerItem](../mfc/reference/coleserveritem-class.md)。 类的对象派生自`CDocItem`表示文档的某些部分。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)
