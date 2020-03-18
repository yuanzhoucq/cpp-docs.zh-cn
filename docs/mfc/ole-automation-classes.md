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
ms.openlocfilehash: 644a4930eb55636ba6e87b949ed610b725334661
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447679"
---
# <a name="ole-automation-classes"></a>OLE 自动化类

这些类支持自动化客户端（控制其他应用程序的应用程序）。 自动化服务器（可由其他应用程序控制的应用程序）通过[调度映射](../mfc/reference/dispatch-maps.md)得到支持。

[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)<br/>
用于从自动化客户端调用自动化服务器。 添加类时，此类用于为提供类型库的自动化服务器创建类型安全类。

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
OLE 自动化过程中的错误导致的异常。 自动化异常由自动化服务器引发，由自动化客户端捕获。

## <a name="see-also"></a>另请参阅

[类概述](../mfc/class-library-overview.md)
