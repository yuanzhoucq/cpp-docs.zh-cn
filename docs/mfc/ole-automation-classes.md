---
title: OLE 自动化类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- Automation, classes
- Automation classes [MFC], OLE classes
- OLE Automation [MFC], classes
- Automation classes [MFC]
- OLE Automation [MFC]
ms.assetid: 96e5372b-ff8a-4da1-933b-4d9bbf4dceb3
ms.openlocfilehash: 08e33e1fce3f792e76e2eec4ecb59601c99d9822
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348713"
---
# <a name="ole-automation-classes"></a>OLE 自动化类

这些类支持自动化客户端 （控制其他应用程序的应用程序）。 自动化服务器 （可以由其他应用程序控制的应用程序） 支持通过[调度映射](../mfc/reference/dispatch-maps.md)。

[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)<br/>
用于从自动化客户端调用自动化服务器。 添加类别时，此类用于创建自动化服务器提供的类型库的类型安全类。

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
在 OLE 自动化过程导致错误的异常。 自动化异常由自动化服务器引发，由自动化客户端捕获。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)
