---
title: OLE 服务器类
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 06f5cf0985756506e42c7ad9fde24641b5a0ce93
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619857"
---
# <a name="ole-server-classes"></a>OLE 服务器类

服务器应用程序使用这些类。 服务器文档派生自 `COleServerDoc` 而不是 `CDocument` 。 请注意，因为 `COleServerDoc` 派生自 `COleLinkingDoc` ，所以服务器文档也可以是支持链接的容器。

`COleServerItem`类表示可以嵌入其他文档或链接到的文档或文档部分。

`COleIPFrameWnd`和 `COleResizeBar` 支持就地编辑，而对象在容器中， `COleTemplateServer` 支持创建文档/视图对，以便可以编辑来自其他应用程序的 OLE 对象。

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
用作服务器应用程序文档类的基类。 `COleServerDoc`对象通过与对象的交互来提供大量的服务器支持 `COleServerItem` 。 使用类库的文档/视图体系结构提供了可视编辑功能。

[CDocItem](reference/cdocitem-class.md)<br/>
和的抽象基类 `COleClientItem` `COleServerItem` 。 派生自的类的对象 `CDocItem` 表示文档的各个部分。

[COleServerItem](reference/coleserveritem-class.md)<br/>
用于表示项的 OLE 接口 `COleServerDoc` 。 通常有一个 `COleServerDoc` 对象，表示文档的嵌入部分。 在支持链接到文档部分的服务器中，可以有多 `COleServerItem` 个对象，每个对象都表示指向部分文档的链接。

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
当正在就地编辑服务器文档时，提供视图的框架窗口。

[COleResizeBar](reference/coleresizebar-class.md)<br/>
提供用于就地调整大小的标准用户界面。 此类的对象始终与对象结合使用 `COleIPFrameWnd` 。

[COleTemplateServer](reference/coletemplateserver-class.md)<br/>
用于使用框架的文档/视图体系结构创建文档。 `COleTemplateServer`对象将其大部分工作委托给关联的 `CDocTemplate` 对象。

[COleException](reference/coleexception-class.md)<br/>
OLE 处理失败导致的异常。 此类将由容器和服务器使用。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
