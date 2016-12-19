---
title: "异常类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "异常类"
  - "异常处理, 异常类"
  - "MFC, 异常"
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异常类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类库提供基于类`CException`的异常处理机制。  在其代码应用程序框架使用异常；还允许在你的应用程序中使用它们。  有关更多信息，请参见[处理异常](../mfc/exception-handling-in-mfc.md)。  您可从 `CException`中派生自己的异常类型。  
  
 MFC 提供可派生您自己的异常的异常类以及它支持所有异常的异常类。  
  
 [CException](../mfc/reference/cexception-class.md)  
 所有异常的基类。  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 存档异常。  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 异常由 DAO 数据库操作的故障。  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 异常由 ODBC 数据库处理的故障。  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 面向文件的异常。  
  
 [CMemoryException](../mfc/reference/cmemoryexception-class.md)  
 内存不足异常  
  
 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)  
 异常由使用不支持的功能引起。  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 异常由 OLE 处理的故障引起。  容器和服务器使用该类。  
  
 [COleDispatchException](../mfc/reference/coledispatchexception-class.md)  
 异常由在自动化期间的错误引起。  自动化异常由自动化服务器引发并通过自动化客户端捕获。  
  
 [CResourceException](../mfc/reference/cresourceexception-class.md)  
 异常由失败加载 Windows 资源引起。  
  
 [CUserException](../mfc/reference/cuserexception-class.md)  
 用于停止正在用户启动操作的异常。  通常，在异常抛出前，用户已意识到问题。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)