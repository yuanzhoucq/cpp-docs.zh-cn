---
title: OLE 自动化类
ms.date: 11/04/2016
helpviewer_keywords:
- Automation, classes
- Automation classes [MFC], OLE classes
- OLE Automation [MFC], classes
- Automation classes [MFC]
- OLE Automation [MFC]
ms.assetid: 96e5372b-ff8a-4da1-933b-4d9bbf4dceb3
ms.openlocfilehash: 04cb93b8ce3699b579342d33c0dae77176878379
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625301"
---
# <a name="ole-automation-classes"></a>OLE 自动化类

这些类支持自动化客户端（控制其他应用程序的应用程序）。 自动化服务器（可由其他应用程序控制的应用程序）通过[调度映射](reference/dispatch-maps.md)得到支持。

[COleDispatchDriver](reference/coledispatchdriver-class.md)<br/>
用于从自动化客户端调用自动化服务器。 添加类时，此类用于为提供类型库的自动化服务器创建类型安全类。

[COleDispatchException](reference/coledispatchexception-class.md)<br/>
OLE 自动化过程中的错误导致的异常。 自动化异常由自动化服务器引发，由自动化客户端捕获。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
