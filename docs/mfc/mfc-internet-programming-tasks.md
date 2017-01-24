---
title: "MFC Internet 编程任务 | Microsoft Docs"
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
  - "Internet 应用程序, 起始步骤"
  - "Internet 应用程序, 入门"
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC Internet 编程任务
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本节包含添加 Internet 支持到应用程序的详细步骤。  主题包括如何使用 MFC 类启用 Internet 现有应用程序中的活动，并添加活动文档支持对现有的 COM 组件。  您是否使用最新股票行情，匹兹堡场橄榄球比赛的比分和 Antarctica最新的温度创建文档？  Microsoft 提供多种技术可帮助您执行通过 Internet。  
  
 活动技术包括 ActiveX 控件 \(原来为 OLE\) 和活动文档；在 Internet 上轻松地检索和保存文件的 WinInet ；有效的数据下载的异步名字对象。  Visual C\+\+ 提供向导帮助您快速入门启动应用程序。  有关这些方法简介，请参见 [MFC Internet 编程的基本知识](../mfc/mfc-internet-programming-basics.md) 和 [MFC COM](../mfc/mfc-com.md)。  
  
 您始终希望 FTP 文件，但不了解 Winsock 和网络程序协议？  使用 HTTP、FTP 和gopher，WinInet 类封装了这些协议，提供您可以使用编写在 Internet 上的客户端应用程序下载到文件的简单组函数。  可以使用 WinInet 搜索在硬盘或全球的目录。  可以透明地收集多种不同类型数据，并显示为一个集成的用户接口。  
  
 您已下载大量的数据？  异步名字对象针对大对象具有呈现提供 COM 组件 \(对象模型 \(COM\)\) 解决方案。  还可以异步使用 WinInet。  
  
 下表描述可以使用这些技术的一些操作。  
  
|有|如果要：|应|  
|-------|----------|-------|  
|Web 服务器。|跟踪登录和详细信息的 URL 请求。|编写一筛选器、请求通知的登录事件和 URL 映射。|  
|Web 浏览器|提供动态内容。|创建 ActiveX 控件和活动文档。|  
|基于文档的应用程序。|对 FTP 文件添加支持。|使用 WinInet 或异步名字对象。|  
  
 参见下列主题获取详细信息为了开始：  
  
-   [应用程序设计选择](../mfc/application-design-choices.md)  
  
-   [编写 MFC 应用程序](../mfc/writing-mfc-applications.md)  
  
-   [Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)  
  
-   [升级现有 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)  
  
-   [Internet 上的活动文档](../mfc/active-documents-on-the-internet.md)  
  
-   [Internet 上的异步名字对象](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [测试 Internet 应用程序](../mfc/testing-internet-applications.md)  
  
-   [Internet 安全性](../mfc/internet-security-cpp.md)  
  
## 请参阅  
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)   
 [按任务划分的 Internet 信息](../mfc/internet-information-by-task.md)