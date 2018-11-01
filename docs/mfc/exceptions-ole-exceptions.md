---
title: 异常：OLE 异常
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
ms.openlocfilehash: 2732f571d305fda2b739be02661ab9558f8bc653
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515410"
---
# <a name="exceptions-ole-exceptions"></a>异常：OLE 异常

OLE 中处理异常的技术和工具与处理其他异常的技术和工具是相同的。 异常处理的详细信息，请参阅文章[c + + 异常处理](../cpp/cpp-exception-handling.md)。

所有异常对象都派生自抽象基类 `CException`。 MFC 提供两个用于处理 OLE 异常的类：

- [COleException](../mfc/reference/coleexception-class.md)用于处理一般 OLE 异常。

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md)有关生成和处理 OLE 调度 （自动化） 异常。

这两个类之间的区别在于它们所提供的信息量和使用的场景。 `COleException` 有一个包含异常的 OLE 状态代码的公共数据成员。 `COleDispatchException` 提供更多信息，包括：

- 应用程序特定的错误代码

- 一个错误说明，如“磁盘已满”

- 应用程序可用来为用户提供额外信息的帮助上下文

- 应用程序的帮助文件的名称

- 产生异常的应用程序的名称

`COleDispatchException` 提供更多信息，以使其可以与类似 Microsoft Visual Basic 这样的产品配合使用。 口头错误说明可用于消息框或其他通知中；帮助信息可用于帮助用户对造成异常的情况作出反应。

两个全局函数对应于两个 OLE 异常类： [AfxThrowOleException](../mfc/reference/exception-processing.md#afxthrowoleexception)并[AfxThrowOleDispatchException](../mfc/reference/exception-processing.md#afxthrowoledispatchexception)。 可使用它们分别引发一般 OLE 异常和 OLE 调度异常。

## <a name="see-also"></a>请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)

