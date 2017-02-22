---
title: "MFC 如何简化 Internet 客户端应用程序的创建 | Microsoft Docs"
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
  - "Internet 应用程序, MFC"
  - "Internet 客户端应用程序, MFC"
  - "MFC, Internet 应用程序"
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MFC 如何简化 Internet 客户端应用程序的创建
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 基础类封装 Win32 某些扩展 Internet \(\) 函数为 MFC WinInet 程序员提供熟悉一个上下文。  MFC 提供类 \(从 [CStdioFile](../mfc/reference/cstdiofile-class.md)[CInternetFile](../mfc/reference/cinternetfile-class.md)[CHttpFile](../mfc/reference/chttpfile-class.md)[CGopherFile](../mfc/reference/cgopherfile-class.md)、和\) 派生的三个类。Internet 文件  不仅使这些类检索的以及操作 Internet 熟悉的数据为本地文件使用 `CStdioFile` 的程序员，但这些类可以处理在本地文件和 Internet 文件以一致，透明方法。  
  
 MFC WinInet 类提供与 `CStdioFile` 相同的功能对于在 Internet 上传输的数据。  这些类将 HTTP、FTP 和地鼠的 Internet 协议为高级应用程序编程接口，提供一个快速、直接的路径。使 Internet 应用程序识别。  例如，若要连接到 FTP 服务器仍需要若干步骤在低，但是，作为 MFC 开发人员，您只需进行一次调用 `CInternetSession::GetFTPConnection` 创建该连接。  
  
 此外，MFC WinInet 类提供以下优点：  
  
-   I\/O 缓存  
  
-   数据的类型安全句柄  
  
-   许多函数的默认参数  
  
-   异常处理常规 Internet 的错误  
  
-   打开句柄和将自动清理  
  
## 请参阅  
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [WinInet 如何简化 Internet 客户端应用程序的创建](../mfc/how-wininet-makes-it-easier-to-create-internet-client-applications.md)