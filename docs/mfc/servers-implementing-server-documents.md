---
title: 服务器： 实现服务器文档 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b62de2a1e6cba6ecbb29521518f5442ab002ddf3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381941"
---
# <a name="servers-implementing-server-documents"></a>服务器：实现服务器文档

此文章介绍了成功实现服务器文档，如果未在应用程序向导中指定的 OLE 服务器选项时必须执行的步骤。

#### <a name="to-define-a-server-document-class"></a>若要定义的服务器文档类

1. 从 `COleServerDoc` 而不是 `CDocument` 派生您的文档类。

1. 创建派生自的服务器项类`COleServerItem`。

1. 实现`OnGetEmbeddedItem`服务器文档类的成员函数。

     `OnGetEmbeddedItem` 容器应用程序的用户创建或编辑嵌入的项时调用。 它应返回一个表示整个文档项。 这应为的对象在`COleServerItem`-派生的类。

1. 重写`Serialize`成员函数以序列化文档的内容。 不需要序列化的服务器项的列表，除非正在使用它们来表示在文档中的本机数据。 有关详细信息，请参阅*实现服务器项*一文中[服务器： 服务器项](../mfc/servers-server-items.md)。

创建服务器文档时，框架将自动向 OLE 系统 Dll 注册文档。 这样，若要标识服务器文档的 Dll。

有关详细信息，请参阅[COleServerItem](../mfc/reference/coleserveritem-class.md)并[COleServerDoc](../mfc/reference/coleserverdoc-class.md)中*类库参考*。

## <a name="see-also"></a>请参阅

[服务器](../mfc/servers.md)<br/>
[服务器：服务器项](../mfc/servers-server-items.md)<br/>
[服务器：实现服务器](../mfc/servers-implementing-a-server.md)<br/>
[服务器：实现就地框架窗口](../mfc/servers-implementing-in-place-frame-windows.md)

