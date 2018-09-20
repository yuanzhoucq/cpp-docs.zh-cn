---
title: OLE 自动化类 |Microsoft Docs
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
- Automation, classes
- Automation classes [MFC], OLE classes
- OLE Automation [MFC], classes
- Automation classes [MFC]
- OLE Automation [MFC]
ms.assetid: 96e5372b-ff8a-4da1-933b-4d9bbf4dceb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea35e51296b2fc528657c4dd9f9b9b76b84aae83
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391509"
---
# <a name="ole-automation-classes"></a>OLE 自动化类

这些类支持自动化客户端 （控制其他应用程序的应用程序）。 自动化服务器 （可以由其他应用程序控制的应用程序） 支持通过[调度映射](../mfc/reference/dispatch-maps.md)。

[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)<br/>
用于从自动化客户端调用自动化服务器。 添加类别时，此类用于创建自动化服务器提供的类型库的类型安全类。

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
在 OLE 自动化过程导致错误的异常。 自动化异常由自动化服务器引发，由自动化客户端捕获。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

