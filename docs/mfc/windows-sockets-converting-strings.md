---
title: "Windows 套接字：转换字符串 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "套接字 [C++], 多字节字符串转换问题"
  - "字符串转换, 多字节字符串"
  - "Windows 套接字 [C++], 多字节字符串转换"
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows 套接字：转换字符串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文和两指南手册演示 Windows Sockets 编程的一些问题。  本文包含转换字符串。  其他问题。[Windows 套接字：阻止](../mfc/windows-sockets-blocking.md) [Windows 套接字：字节顺序](../mfc/windows-sockets-byte-ordering.md)和报表。  
  
 如果使用或派生自类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，将需要管理这些问题。  如果使用或派生自类[CSocket](../mfc/reference/csocket-class.md)，MFC 为您管理这些。  
  
## 转换字符串  
 如果在使用的通信使用 ANSI 字符串存储不同的宽字符格式，如 Unicode 或的多字节字符集 \(MBCS\) 应用程序之间，或者是其中一个应用程序之间字符串时，必须管理转换在 `CAsyncSocket`的下面。  `CArchive` 对象使用 `CSocket` 对象来管理类上述转换 [CString](../atl-mfc-shared/reference/cstringt-class.md)的功能。  有关更多信息，请参见 Windows 套接字规范，位于 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
 有关详细信息，请参阅：  
  
-   [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
## 请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)