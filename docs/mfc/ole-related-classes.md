---
title: OLE 相关类
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: 6f6db6ce133b440a5ed86e7c1642396888744540
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621024"
---
# <a name="ole-related-classes"></a>OLE 相关类

这些类提供了许多不同的服务，从异常到文件输入和输出。

[COleObjectFactory](reference/coleobjectfactory-class.md)<br/>
用于从其他容器请求时创建项。 此类充当更多特定工厂类型的基类，包括 `COleTemplateServer`。

[COleMessageFilter](reference/colemessagefilter-class.md)<br/>
用于管理与 OLE 轻量远程过程调用 (LRPC) 的并发。

[COleStreamFile](reference/colestreamfile-class.md)<br/>
使用 COM `IStream` 接口为 `CFile` 提供对复合文件的访问权限。 此类（派生自 `CFile`）使 MFC 序列化能够使用 OLE 结构化存储。

[CRectTracker](reference/crecttracker-class.md)<br/>
用于允许就地项的移动、重设大小和重新定位。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
