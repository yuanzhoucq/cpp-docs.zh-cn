---
title: OLE 容器类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfdff6023beeedfa14d37e5b404fa3c223691b85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ole-container-classes"></a>OLE 容器类
容器应用程序使用这些类。 同时`COleLinkingDoc`和`COleDocument`管理的集合`COleClientItem`对象。 而不是派生您的文档类从**CDocument**，你将从它派生`COleLinkingDoc`或`COleDocument`，取决于是否要支持链接到嵌入到文档中的对象。  
  
 使用`COleClientItem`对象表示文档中嵌入从另一个文档或是另一个文档的链接中每个 OLE 项。  
  
 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)  
 支持活动文档包容。  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 用于复合文档实现以及基本容器支持。 可用作一个用于类派生自`CDocItem`。 此类可以用作基类的容器时记录该对象，并且是类的基类`COleServerDoc`。  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 从派生的类`COleDocument`为链接提供基础结构。 应为此类，而不是从容器应用程序中派生文档类`COleDocument`如果你希望它们以支持链接到嵌入对象。  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 维护 rich edit 控件中的 OLE 客户端项的列表。 与使用[CRichEditView](../mfc/reference/cricheditview-class.md)和[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 抽象基类的`COleClientItem`和`COleServerItem`。 对象的类派生自`CDocItem`表示文档的某些部分。  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md)  
 一个表示与某一嵌入或链接 OLE 项的连接的客户端的一端的客户端项类。 从此类派生您的客户端项。  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 提供对项存储在 rich edit 控件一起使用时的 OLE 客户端访问`CRichEditView`和`CRichEditDoc`。  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 OLE 处理失败导致的异常。 此类将由容器和服务器使用。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

