---
title: "异常：OLE 异常 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "异常处理, OLE"
  - "异常, OLE"
  - "OLE 异常"
  - "OLE 异常, 用于处理的类"
  - "OLE, 异常"
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异常：OLE 异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

处理OLE异常的技术和设备与处理其他异常的相同。  更多有关异常处理的信息，请参见文章[C\+\+ 异常处理](../cpp/cpp-exception-handling.md)。  
  
 所有异常对象都是从抽象基类`CException`中派生而来。  MFC 提供两种处理OLE异常的途径：  
  
-   [COleException](../mfc/reference/coleexception-class.md)用于处理一般的OLE 异常。  
  
-   [COleDispatchException](../mfc/reference/coledispatchexception-class.md)用于生成和操作OLE调度\( 自动化\) 异常。  
  
 这两个类他们所提供的信息量与使用的场景都有差别。  `COleException` 中有包含异常OLE状态代码的公共数据成员。  `COleDispatchException` 提供更多信息，包括：  
  
-   应用程序的特定错误代码  
  
-   一个错误的描述信息，如“磁盘已满”  
  
-   你的应用程序可以通过帮助上下文来为用户提供额外的信息。  
  
-   应用程序的帮助文件的名称  
  
-   产生异常的应用程序的名称。  
  
 `COleDispatchException` 可以提供的信息更多，所以其可以与像Microsoft Visual Basic这样的产品配合使用。  错误说明可以用于消息框或其他通知中；帮助信息可用于帮助用户对造成异常的条件作出反应。  
  
 两个全局函数对应于两个OLE 类异常类：[AfxThrowOleException](../Topic/AfxThrowOleException.md) 和 [AfxThrowOleDispatchException](../Topic/AfxThrowOleDispatchException.md)。  使用它们各自地抛出OLE一般异常和OLE调度异常。  
  
## 请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)