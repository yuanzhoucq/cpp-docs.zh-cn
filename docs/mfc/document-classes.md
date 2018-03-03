---
title: "文档类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.document
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a2436b46b7486bd30398dffc530d2adea3d2e48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="document-classes"></a>文档类
创建的文档模板对象的文档类对象管理应用程序的数据。 从这些类之一，将为你的文档中派生一个类。  
  
 文档类对象与视图对象交互。 视图对象表示一个窗口的工作区、 显示文档的数据，并允许用户与之进行交互。 文档模板对象创建文档和视图。  
  
 [CDocument](../mfc/reference/cdocument-class.md)  
 应用程序特定文档的基类。 派生文档类的类**CDocument**。  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 用于复合文档实现以及基本容器支持。 可用作一个用于类派生自[CDocItem](../mfc/reference/cdocitem-class.md)。 此类可以用作基类的容器时记录该对象，并且是类的基类`COleServerDoc`。  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 从派生的类`COleDocument`为链接提供基础结构。 应为此类，而不是从容器应用程序中派生文档类`COleDocument`如果你希望它们以支持链接到嵌入对象。  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 维护 rich edit 控件中的 OLE 客户端项的列表。 与使用[CRichEditView](../mfc/reference/cricheditview-class.md)和[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 服务器应用程序文档类用作基类。 `COleServerDoc`对象提供通过与交互的服务器支持大量[COleServerItem](../mfc/reference/coleserveritem-class.md)对象。 使用类库的文档/视图体系结构提供可视编辑功能。  
  
 [CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)  
 提供，与[CHtmlEditView](../mfc/reference/chtmleditview-class.md)，MFC 文档视图体系结构上下文中的 WebBrowser HTML 编辑平台功能。  
  
## <a name="related-classes"></a>相关的类  
 文档类对象可以是永久性的-换而言之，它们可以将其状态写入到存储媒体和读回。 MFC 提供了`CArchive`类，以便将文档的数据传输到存储媒体。  
  
 [CArchive](../mfc/reference/carchive-class.md)  
 配合[CFile](../mfc/reference/cfile-class.md)对象来实现通过序列化的对象的持久存储 (请参阅[cobject:: Serialize](../mfc/reference/cobject-class.md#serialize))。  
  
 文档还可以包含 OLE 对象。 `CDocItem`是服务器和客户端项的基类。  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 抽象基类的[COleClientItem](../mfc/reference/coleclientitem-class.md)和[COleServerItem](../mfc/reference/coleserveritem-class.md)。 对象的类派生自`CDocItem`表示文档的某些部分。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

