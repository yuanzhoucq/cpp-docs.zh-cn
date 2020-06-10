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
ms.openlocfilehash: 7bd0b0cb2c9eb6fe49356ae8fd4602676d54fa66
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622786"
---
# <a name="exceptions-ole-exceptions"></a>异常：OLE 异常

OLE 中处理异常的技术和工具与处理其他异常的技术和工具是相同的。 有关异常处理的详细信息，请参阅本文[最新的 c + + 有关异常和错误处理的最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)。

所有异常对象都派生自抽象基类 `CException`。 MFC 提供两个用于处理 OLE 异常的类：

- [COleException](reference/coleexception-class.md)用于处理常规 OLE 异常。

- [COleDispatchException](reference/coledispatchexception-class.md)用于生成和处理 OLE 调度（自动化）异常。

这两个类之间的区别在于它们所提供的信息量和使用的场景。 `COleException` 有一个包含异常的 OLE 状态代码的公共数据成员。 `COleDispatchException` 提供更多信息，包括：

- 应用程序特定的错误代码

- 一个错误说明，如“磁盘已满”

- 应用程序可用来为用户提供额外信息的帮助上下文

- 应用程序的帮助文件的名称

- 产生异常的应用程序的名称

`COleDispatchException` 提供更多信息，以使其可以与类似 Microsoft Visual Basic 这样的产品配合使用。 口头错误说明可用于消息框或其他通知中；帮助信息可用于帮助用户对造成异常的情况作出反应。

两个全局函数对应于两个 OLE 异常类： [AfxThrowOleException](reference/exception-processing.md#afxthrowoleexception)和[AfxThrowOleDispatchException](reference/exception-processing.md#afxthrowoledispatchexception)。 可使用它们分别引发一般 OLE 异常和 OLE 调度异常。

## <a name="see-also"></a>另请参阅

[异常处理](exception-handling-in-mfc.md)
