---
title: OLE 相关类 |Microsoft 文档
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
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: baa4ec3de21ce91e0d8723ad0e4debb39a26b3cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348510"
---
# <a name="ole-related-classes"></a>OLE 相关类
这些类提供了许多不同的服务，从异常到文件输入和输出。  
  
 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)  
 用于从其他容器请求时创建项。 此类充当更多特定工厂类型的基类，包括 `COleTemplateServer`。  
  
 [COleMessageFilter](../mfc/reference/colemessagefilter-class.md)  
 用于管理与 OLE 轻量远程过程调用 (LRPC) 的并发。  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 使用 COM `IStream` 接口为 `CFile` 提供对复合文件的访问权限。 此类（派生自 `CFile`）使 MFC 序列化能够使用 OLE 结构化存储。  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 用于允许就地项的移动、重设大小和重新定位。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

