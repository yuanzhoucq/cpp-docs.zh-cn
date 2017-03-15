---
title: "典型 Internet 客户端应用程序中的步骤 | Microsoft Docs"
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
  - "Internet 应用程序, 客户端应用程序"
  - "Internet 客户端应用程序, 常规表"
  - "WinInet 类, 编程"
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 典型 Internet 客户端应用程序中的步骤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表显示在典型的 Internet 客户端应用程序便可能执行还原的步骤。  
  
|目标|采取的操作|效果|  
|--------|-----------|--------|  
|启动 Internet 会话。|创建 [CInternetSession](../mfc/reference/cinternetsession-class.md) 对象。|初始化 WinInet 并连接到服务器。|  
|设置查询选项 \(例如 Internet 重试的超时限制，或数字\)。|使用 [CInternetSession::SetOption](../Topic/CInternetSession::SetOption.md)。|如果操作不成功，返回FALSE。|  
|建立回调函数来监视会话的状态。|使用 [CInternetSession::EnableStatusCallback](../Topic/CInternetSession::EnableStatusCallback.md)。|建立回调到 [CInternetSession::OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md)。  重写 `OnStatusCallback` 创建自己的回调例程。|  
|服务器连接到 Internet、Intranet 服务器或本地文件。|使用 [CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md)。|分析 URL 并打开到指定服务器的连接。  \(如果通过本地 `OpenURL` 的文件名\)，返回。[CStdioFile](../mfc/reference/cstdiofile-class.md) 这是可以访问文件或从服务器检索的数据的对象。|  
|从文件中读取|使用 [CInternetFile::Read](../Topic/CInternetFile::Read.md)。|读取指定的字节数，则使用提供的缓冲区。|  
|处理异常。|使用 [CInternetException](../mfc/reference/cinternetexception-class.md) 类。|处理所有公共 Internet 异常类型。|  
|关闭 Internet 会话。|处理 [CInternetSession](../mfc/reference/cinternetsession-class.md) 对象。|自动清理打开文件句柄和连接。|  
  
## 请参阅  
 [Win32 Internet 扩展 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Internet 客户端类的必备条件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 类编写 Internet 客户端应用程序](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)