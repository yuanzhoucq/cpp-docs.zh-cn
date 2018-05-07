---
title: OLE 服务器类 |Microsoft 文档
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
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fc737a3d11307dff917132bfd113896b4ad801f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ole-server-classes"></a>OLE 服务器类
服务器应用程序使用这些类。 服务器文档派生自`COleServerDoc`而不是从**CDocument**。 请注意，因为`COleServerDoc`派生自`COleLinkingDoc`，服务器文档也可以是支持将链接的容器。  
  
 `COleServerItem`类表示文档或文档，可以在另一个文档中嵌入或链接到的一部分。  
  
 `COleIPFrameWnd` 和`COleResizeBar`支持就地编辑时的对象处于一个容器，和`COleTemplateServer`支持的文档/视图对创建，这样就可以编辑从其他应用程序的 OLE 对象。  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 服务器应用程序文档类用作基类。 `COleServerDoc` 对象提供通过与交互的服务器支持大量`COleServerItem`对象。 使用类库的文档/视图体系结构提供可视编辑功能。  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 抽象基类的`COleClientItem`和`COleServerItem`。 对象的类派生自`CDocItem`表示文档的某些部分。  
  
 [COleServerItem](../mfc/reference/coleserveritem-class.md)  
 用于表示的 OLE 接口`COleServerDoc`项。 通常会有一个`COleServerDoc`对象，用于表示文档的嵌入的一部分。 中支持链接到文档的某些部分的服务器，可以有许多`COleServerItem`对象，其中每个表示链接到文档的一部分。  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 当就地编辑时的服务器文档提供视图框架窗口。  
  
 [COleResizeBar](../mfc/reference/coleresizebar-class.md)  
 提供用于就地调整大小的标准用户界面。 此类的对象始终使用结合`COleIPFrameWnd`对象。  
  
 [COleTemplateServer](../mfc/reference/coletemplateserver-class.md)  
 用于创建使用框架的文档/视图体系结构的文档。 A`COleTemplateServer`对象委托关联到其工作中的大部分`CDocTemplate`对象。  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 OLE 处理失败导致的异常。 此类将由容器和服务器使用。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

