---
title: 服务器： 实现服务器文档 |Microsoft 文档
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
ms.openlocfilehash: 273fd1e5afefb8a10b3e1ae8e3c2f81ccec05e7f
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950823"
---
# <a name="servers-implementing-server-documents"></a>服务器：实现服务器文档
此文章介绍了您必须执行以便成功实现服务器文档，如果你未在应用程序向导中指定的 OLE 服务器选项的步骤。  
  
#### <a name="to-define-a-server-document-class"></a>若要定义服务器文档类  
  
1.  从 `COleServerDoc` 而不是 `CDocument` 派生您的文档类。  
  
2.  创建派生自某个服务器项类`COleServerItem`。  
  
3.  实现`OnGetEmbeddedItem`你服务器文档类的成员函数。  
  
     `OnGetEmbeddedItem` 容器应用程序的用户创建或编辑嵌入的项时调用。 它应返回一个表示整个文档的项。 这应是一个你`COleServerItem`-派生类。  
  
4.  重写`Serialize`成员函数要序列化文档的内容。 不需要序列化的服务器项的列表，除非你正在使用它们来表示在文档中的本机数据。 有关详细信息，请参阅*实现服务器项*文章中[服务器： 服务器项](../mfc/servers-server-items.md)。  
  
 创建的服务器文档时，框架将自动使用 OLE 系统 Dll 注册文档。 这允许 Dll 能够识别服务器文档。  
  
 有关详细信息，请参阅[COleServerItem](../mfc/reference/coleserveritem-class.md)和[COleServerDoc](../mfc/reference/coleserverdoc-class.md)中*类库参考*。  
  
## <a name="see-also"></a>请参阅  
 [服务器](../mfc/servers.md)   
 [服务器： 服务器项](../mfc/servers-server-items.md)   
 [服务器： 实现服务器](../mfc/servers-implementing-a-server.md)   
 [服务器：实现就地框架窗口](../mfc/servers-implementing-in-place-frame-windows.md)

