---
title: OLE 容器类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 518ae4889a2c5d9dae10e5b5cba6845010ba883c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517138"
---
# <a name="ole-container-classes"></a>OLE 容器类

容器应用程序使用这些类。 这两`COleLinkingDoc`并`COleDocument`管理的集合`COleClientItem`对象。 而不是派生您的文档类从`CDocument`，你将从中进行派生`COleLinkingDoc`或`COleDocument`，取决于是否需要支持为链接到嵌入到文档中的对象。

使用`COleClientItem`对象来表示文档的另一个文档中嵌入或链接到另一个文档中的每个 OLE 项。

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
支持活动文档包容。

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
用于复合文档实现，以及基本容器支持。 从派生类的容器用作`CDocItem`。 此类可以用作基类，为容器记录，并且是类的基类`COleServerDoc`。

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
一个类派生自`COleDocument`为链接提供了基础结构。 应为此类，而不是从容器应用程序派生文档类`COleDocument`如果你希望它们以支持链接到嵌入对象。

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
维护格式文本编辑控件中的 OLE 客户端项的列表。 用于[CRichEditView](../mfc/reference/cricheditview-class.md)并[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
抽象类的基类`COleClientItem`和`COleServerItem`。 类的对象派生自`CDocItem`表示文档的某些部分。

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
一个表示与嵌入或链接 OLE 项的连接的客户端的端的客户端项类。 从此类派生您的客户端项。

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
提供 OLE 项存储在 rich edit 控件一起使用时对客户端的访问权限`CRichEditView`和`CRichEditDoc`。

[COleException](../mfc/reference/coleexception-class.md)<br/>
OLE 处理失败导致的异常。 此类将由容器和服务器使用。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

