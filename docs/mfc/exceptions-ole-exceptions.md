---
title: "异常： OLE 异常 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 67be1947b3fa08c26d659838922ce42a905167a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-ole-exceptions"></a>异常：OLE 异常
OLE 中处理异常的技术和工具与处理其他异常的技术和工具是相同的。 异常处理的详细信息，请参阅文章[c + + 异常处理](../cpp/cpp-exception-handling.md)。  
  
 所有异常对象都派生自抽象基类 `CException`。 MFC 提供两个用于处理 OLE 异常的类：  
  
-   [COleException](../mfc/reference/coleexception-class.md)用于处理一般 OLE 异常。  
  
-   [COleDispatchException](../mfc/reference/coledispatchexception-class.md)的生成和处理 OLE 调度 （自动化） 异常。  
  
 这两个类之间的区别在于它们所提供的信息量和使用的场景。 `COleException` 有一个包含异常的 OLE 状态代码的公共数据成员。 `COleDispatchException` 提供更多信息，包括：  
  
-   应用程序特定的错误代码  
  
-   一个错误说明，如“磁盘已满”  
  
-   应用程序可用来为用户提供额外信息的帮助上下文  
  
-   应用程序的帮助文件的名称  
  
-   产生异常的应用程序的名称  
  
 `COleDispatchException` 提供更多信息，以使其可以与类似 Microsoft Visual Basic 这样的产品配合使用。 口头错误说明可用于消息框或其他通知中；帮助信息可用于帮助用户对造成异常的情况作出反应。  
  
 两个全局函数对应于两个 OLE 异常类： [AfxThrowOleException](../mfc/reference/exception-processing.md#afxthrowoleexception)和[AfxThrowOleDispatchException](../mfc/reference/exception-processing.md#afxthrowoledispatchexception)。 可使用它们分别引发一般 OLE 异常和 OLE 调度异常。  
  
## <a name="see-also"></a>请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)

