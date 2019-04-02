---
title: 服务器：服务器项
ms.date: 11/04/2016
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
ms.openlocfilehash: abee619aa921b3e036a2bbeb1b4f5ae08d83f5bb
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767894"
---
# <a name="servers-server-items"></a>服务器：服务器项

当容器启动服务器以便用户可编辑嵌入或链接的 OLE 项时，服务器应用程序将创建一个“服务器项”。 服务器项是派生自 `COleServerItem` 的类的对象，可提供服务器文档和容器应用程序之间的接口。

`COleServerItem` 类定义由 OLE 调用的若干可重写的成员函数，通常用于响应容器的请求。 服务器项可以表示服务器文档的一部分或整个文档。 将 OLE 项嵌入到容器文档中时，服务器项表示整个服务器文档。 链接 OLE 项时，服务器项可以表示服务器文档的一部分或整个文档，这取决于是链接到部分文档还是整个文档。

在中[HIERSVR](../overview/visual-cpp-samples.md)示例，例如，服务器项类`CServerItem`，有一个成员是指向类的对象的指针， `CServerNode`。 `CServerNode`对象是 HIERSVR 应用程序的文档，这是一个树中的节点。 当`CServerNode`对象是根节点，`CServerItem`对象表示整个文档。 当`CServerNode`对象是子节点，`CServerItem`对象表示文档的一部分。 请参阅 MFC OLE 示例[HIERSVR](../overview/visual-cpp-samples.md)有关这种交互的示例。

##  <a name="_core_implementing_server_items"></a> 实现服务器项

如果使用应用程序向导生成应用程序的“起始”代码，若要在起始代码中包含服务器项，则只需从“OLE 选项”页中选择一个服务器选项即可。 如果您要将服务器项添加到现有应用程序中，请执行以下步骤：

#### <a name="to-implement-a-server-item"></a>实现服务器项

1. 从 `COleServerItem` 派生一个类。

1. 在派生类中，重写 `OnDraw` 成员函数。

   框架调用 `OnDraw` 以将 OLE 项渲染到图元文件中。 容器应用程序可使用此图元文件渲染该项。 应用程序的视图类还有一个 `OnDraw` 成员函数，在服务器应用程序处于活动状态时可使用此成员函数渲染该项。

1. 为服务器文档类实现 `OnGetEmbeddedItem` 的重写。 有关详细信息，请参阅文章[服务器：实现服务器文档](../mfc/servers-implementing-server-documents.md)和 MFC OLE 示例[HIERSVR](../overview/visual-cpp-samples.md)。

1. 实现服务器项类的 `OnGetExtent` 成员函数。 框架调用此函数来检索项的大小。 默认实现不执行任何操作。

##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> 服务器项体系结构的提示

如中所述[实现服务器项](#_core_implementing_server_items)，服务器应用程序必须能够呈现项目中的服务器的视图和容器应用程序使用的图元文件中。 Microsoft 基础类库的应用程序体系结构中，视图类的`OnDraw`成员函数时正在编辑渲染项 (请参阅[cview:: Ondraw](../mfc/reference/cview-class.md#ondraw)中*类库参考*). 服务器项`OnDraw`渲染到图元文件中所有其他情况下的项 (请参阅[coleserveritem:: Ondraw](../mfc/reference/coleserveritem-class.md#ondraw))。

你可以通过在服务器文档类中编写 Helper 函数，并在你的视图类和服务器项类中从 `OnDraw` 函数调用 Helper 函数来避免重复代码。 MFC OLE 示例[HIERSVR](../overview/visual-cpp-samples.md)使用此策略： 函数`CServerView::OnDraw`并`CServerItem::OnDraw`都将调用`CServerDoc::DrawTree`渲染该项。

因为视图和项是在不同条件下绘制的，所以视图和项都具有 `OnDraw` 成员函数。 视图必须考虑这些因素，如缩放、选择大小和范围、剪辑和用户界面元素（如滚动条）。 另一方面，服务器项始终绘制整个 OLE 对象。

有关详细信息，请参阅[cview:: Ondraw](../mfc/reference/cview-class.md#ondraw)， [COleServerItem](../mfc/reference/coleserveritem-class.md)， [coleserveritem:: Ondraw](../mfc/reference/coleserveritem-class.md#ondraw)，和[COleServerDoc::OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)中*类库参考*。

## <a name="see-also"></a>请参阅

[服务器](../mfc/servers.md)
