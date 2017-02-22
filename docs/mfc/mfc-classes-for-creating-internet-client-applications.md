---
title: "用于创建 Internet 客户端应用程序的 MFC 类 | Microsoft Docs"
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
  - "类 [C++], MFC"
  - "Internet 应用程序, MFC"
  - "Internet 客户端应用程序, MFC"
  - "MFC, WinInet 类"
  - "WinInet 类, 类"
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 用于创建 Internet 客户端应用程序的 MFC 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供 Internet 编写客户端应用程序提供下列类和全局函数。  缩进指示类从上面的 unindented 类派生。  例如，`CGopherFile`和`CHttpFile` 派生自  `CInternetFile`。  这些类和全局函数在 AFXINET.H 声明，不过 `CFileFind`除外，在 AFX.H. 声明。  
  
## 类  
  
-   [CInternetSession](../mfc/reference/cinternetsession-class.md)  
  
-   [CInternetConnection](../mfc/reference/cinternetconnection-class.md)  
  
    -   [CFtpConnection](../mfc/reference/cftpconnection-class.md)  
  
    -   [CGopherConnection](../mfc/reference/cgopherconnection-class.md)  
  
    -   [CHttpConnection](../mfc/reference/chttpconnection-class.md)  
  
-   [CInternetFile](../mfc/reference/cinternetfile-class.md)  
  
    -   [CGopherFile](../mfc/reference/cgopherfile-class.md)  
  
    -   [CHttpFile](../mfc/reference/chttpfile-class.md)  
  
-   [CFileFind](../mfc/reference/cfilefind-class.md)  
  
    -   [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)  
  
    -   [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)  
  
-   [CGopherLocator](../mfc/reference/cgopherlocator-class.md)  
  
-   [CInternetException](../mfc/reference/cinternetexception-class.md)  
  
## 全局函数  
  
-   [AfxParseURL](../Topic/AfxParseURL.md)  
  
-   [AfxGetInternetHandleType](../Topic/AfxGetInternetHandleType.md)  
  
-   [AfxThrowInternetException](../Topic/AfxThrowInternetException.md)  
  
## 请参阅  
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)