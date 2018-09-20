---
title: OLE 服务器类 |Microsoft Docs
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
ms.openlocfilehash: 9994cdadb0ca2924a3ac773752ae40f3a750b74f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442885"
---
# <a name="ole-server-classes"></a>OLE 服务器类

服务器应用程序使用这些类。 服务器文档派生自`COleServerDoc`而不是从`CDocument`。 请注意，由于`COleServerDoc`派生自`COleLinkingDoc`，服务器文档也可以是支持将链接的容器。

`COleServerItem`类表示文档或文档可以在另一个文档中嵌入或链接到的一部分。

`COleIPFrameWnd` 并`COleResizeBar`支持就地编辑在一个容器，该对象时和`COleTemplateServer`支持的文档/视图对创建，这样就可以编辑 OLE 对象从其他应用程序。

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
用作服务器应用程序文档类的基类。 `COleServerDoc` 对象提供的服务器支持与交互通过大容量`COleServerItem`对象。 使用类库的文档/视图体系结构提供可视编辑功能。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
抽象类的基类`COleClientItem`和`COleServerItem`。 类的对象派生自`CDocItem`表示文档的某些部分。

[COleServerItem](../mfc/reference/coleserveritem-class.md)<br/>
用于表示的 OLE 接口`COleServerDoc`项。 通常会有一个`COleServerDoc`对象，表示文档的嵌入的部分。 在服务器中的支持链接到文档的某些部分，可以有许多`COleServerItem`对象，其中每个表示链接到文档的一部分。

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
正在就地编辑服务器文档时，应提供视图框架窗口。

[COleResizeBar](../mfc/reference/coleresizebar-class.md)<br/>
提供用于就地调整大小标准用户界面。 此类的对象始终结合使用`COleIPFrameWnd`对象。

[COleTemplateServer](../mfc/reference/coletemplateserver-class.md)<br/>
用于创建使用框架的文档/视图体系结构文档。 一个`COleTemplateServer`对象将委托关联到其工作的大部分`CDocTemplate`对象。

[COleException](../mfc/reference/coleexception-class.md)<br/>
OLE 处理失败导致的异常。 此类将由容器和服务器使用。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

