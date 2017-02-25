---
title: "Windows 套接字类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.net"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "套接字类"
  - "Windows 套接字 [C++], 类"
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Windows 套接字类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Windows 套接字提供一个在两台计算机间的通信与网络协议无关的方法。  这些套接字能同步 \(程序等待直到完成通信\) 或异步 \(当通信进行时，程序继续运行\)。  
  
 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)  
 在一个小的包装内封装 Windows 套接字 API。  
  
 [CSocket](../mfc/reference/csocket-class.md)  
 从 `CAsyncSocket`派生的更高级别的抽象。  它同步运行。  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 提供一个 `CFile` 接口给 Windows 套接字。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)